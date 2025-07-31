pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/umamahesh571/Jenkins-sample-pipeline-example.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
    }

    post {
        success {
            echo '✅ Build completed successfully!'
            emailext(
                subject: "✅ SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: """<p>Build succeeded for job: ${env.JOB_NAME}</p>
                         <p>Build Number: ${env.BUILD_NUMBER}</p>
                         <p>View it: <a href='${env.BUILD_URL}'>${env.BUILD_URL}</a></p>""",
                to: 'umamahesh571@gail.com',
                mimeType: 'text/html'
            )
       
        failure {
            echo '❌ Build failed!'
            emailext(
                subject: "❌ FAILURE: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: """<p>Build failed for job: ${env.JOB_NAME}</p>
                         <p>Build Number: ${env.BUILD_NUMBER}</p>
                         <p>View logs: <a href='${env.BUILD_URL}'>${env.BUILD_URL}</a></p>""",
                to: 'umamahesh571@gmail.com',
                mimeType: 'text/html'
            )
        }
    }
}
