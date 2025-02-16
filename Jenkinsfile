pipeline {
    agent any

    stages {
        stage('AWS') {
            agent {
                docker{
                    image 'amazon/aws-cli'
                    args "--entrypoint=''"
                }
            }
            steps {
                withCredentials([usernamePassword(credentialsId: 'my-aws', passwordVariable: 'AWS_SECRET_ACCESS_KEY', usernameVariable: 'AWS_ACCESS_KEY_ID')]) {
                sh '''
                aws --version
                echo "Hello S3!" > index.html
                aws s3 cp index.html s3://jenkins-learning-160220251748/index.html

                '''
                    }
               
            }
        }
    }
}
