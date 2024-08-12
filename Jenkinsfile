
pipeline {
    agent any

    environment {
        // Define environment variables here if needed
    }

    stages {
        stage('Preparation') {
            steps {
                script {
                    // Get the current branch name
                    def branchName = env.BRANCH_NAME
                    echo "Building branch: ${branchName}"
                    
                    // Set different variables or configurations based on branch name
                    if (branchName.startsWith('sprint-')) {
                        env.SPRINT_NUMBER = branchName.replace('sprint-', '')
                    } else {
                        error "Branch name does not match the expected pattern."
                    }
                }
            }
        }

        stage('Build') {
            steps {
                echo "Building Sprint ${env.SPRINT_NUMBER}"
                // Add your build steps here
            }
        }

        stage('Test') {
            steps {
                echo "Testing Sprint ${env.SPRINT_NUMBER}"
                // Add your test steps here
            }
        }

        stage('Deploy') {
            when {
                // Only deploy on specific branches if needed
                branch 'main'
            }
            steps {
                echo "Deploying Sprint ${env.SPRINT_NUMBER}"
                // Add your deploy steps here
            }
        }
    }

    post {
        success {
            echo "Build and tests successful for Sprint ${env.SPRINT_NUMBER}"
        }
        failure {
            echo "Build or tests failed for Sprint ${env.SPRINT_NUMBER}"
        }
        always {
            echo "Cleaning up after build"
            // Add any cleanup steps here
        }
    }
}
