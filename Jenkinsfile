pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-phani', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://FFE4352451383EA5F4E2A1E9BAE5B61E.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-phani', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://FFE4352451383EA5F4E2A1E9BAE5B61E.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
