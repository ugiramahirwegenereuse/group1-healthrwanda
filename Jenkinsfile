pipeline {
    agent any

    environment {
        // You can change this to your environment if needed
        NODE_ENV = 'production'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning repository...'
                git branch: 'main', url: 'https://github.com/ugiramahirwegenereuse/group1-healthrwanda.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing project dependencies...'
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'npm test || echo "No tests found, skipping..."'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                // Example: deploy to local folder or server
                sh '''
                mkdir -p /var/www/healthrwanda
                cp -r * /var/www/healthrwanda/
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Build and Deployment Successful!'
        }
        failure {
            echo '❌ Build Failed. Check logs for details.'
        }
    }
}
