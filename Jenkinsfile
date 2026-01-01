pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/sathish159357/Devops-2.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-ci-app:latest .'
            }
        }

        stage('Run Container Test') {
            steps {
                sh '''
                docker run -d -p 5000:5000 devops-ci-app:latest
                sleep 5
                curl http://localhost:5000
                '''
            }
        }
    }
}
