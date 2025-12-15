pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/taha1712/jenkins-azure-demo.git'

            }
        }

        stage('Install Node') {
            steps {
                bat '''
                where node || powershell -Command "Invoke-WebRequest https://nodejs.org/dist/v18.17.0/node-v18.17.0-x64.msi -OutFile node.msi"
                if exist node.msi msiexec /i node.msi /qn
                '''
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install || echo No dependencies found'
            }
        }

        stage('Run App') {
            steps {
                bat 'start cmd /c "node app.js"'
            }
        }
    }
}
