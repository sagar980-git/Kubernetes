#Pipeline code 

pipeline { 
	agent any
	stages {
		stage('Checking EKS Access') {
			steps {
				withAWS(credentials: 'aws-creds') {
					sh 'aws eks update-kubeconfig --region us-east-1  --name eks-cluster-1'
					sh 'kubectl get pods -A'
				}
			}
		}
		stage('Creating EKS Namespaces') {
		    steps {
			    withAWS(credentials: 'aws-creds') {
				    sh 'aws eks update-kubeconfig --region us-east-1  --name eks-cluster-1'
				    sh 'kubectl create ns development || exit 0'
				    sh 'kubectl create ns production || exit 0'
			    }
		    }
    	}
	}		
}