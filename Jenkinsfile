pipeline {
  agent any
  parameters {
    string(name: 'JAR_PATH', defaultValue: '', description: 'Add path to Artifact')
  }

  stages {
    stage("Deploy") {
			agent {
        		docker {
        			image 'govau/cf-cli'
        		}
    		}
			environment {
				CLOUD_FOUNDARY_LOGIN = credentials('CLOUD_FOUNDARY_LOGIN')
			}
			steps {
				echo 'Deploying FitnessViking'
        sh 'cf login -a https://api.run.pivotal.io -u ${CLOUD_FOUNDARY_LOGIN_USR} -p ${CLOUD_FOUNDARY_LOGIN_PSW}'
        sh 'cf push -p $params.JAR_PATH'
        }
	    }
   }
}
