pipeline {
	agent any

    options {
        buildDiscarder(logRotator(numToKeepStr:'5'))
    }

	environment {
        PATH = "$PATH:/home/paolo/Documents/apache-jmeter-3.3/bin/"
    }

	stages {
	    stage('API Test') {
			steps {
	    		timeout(time: 10, unit:'MINUTES'){
		    		echo "API Test execution"
   				}
	    	}
	    }
    	stage('Performance Test') {
    		steps {
				timeout(time:10, unit:'MINUTES'){
					sh 'jmeter -n -t ./Presentation_example.jmx -l ./report.jtl'
					perfReport '*report.jtl'
				}
    		}
    	}
    	stage('Mining') {
    		steps {
    			echo "Mining Both Reports"
    		}
    	}
   }
}
