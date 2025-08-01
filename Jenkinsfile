pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/YOUR_USERNAME/YOUR_REPO.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'python3 -m venv venv'
                sh '. venv/bin/activate && pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                sh '. venv/bin/activate && mkdir -p reports && pytest tests/ --junitxml=reports/results.xml'
            }
        }

        stage('Publish Test Results') {
            steps {
                junit 'reports/results.xml'
            }
        }
    }
}

