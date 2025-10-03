pipeline {
    agent any

    environment {
        VENV = "venv"
    }

    stages {
        stage('Build') {
            steps {
                sh 'python3 -m venv venv'
                sh './venv/bin/pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                sh './venv/bin/pytest'
            }
        }

        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                echo 'Deploying Flask app to staging...'
                // Example: sh 'bash deploy.sh'
            }
        }
    }

    post {
        success {
            echo 'Build Succeeded!'
        }
        failure {
            echo 'Build Failed!'
        }
    }
}
