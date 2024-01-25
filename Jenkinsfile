node('built-in') 
{
    stage('ContinousDownload') 
    {
        git 'https://github.com/ANYA-123/maven.git'
    }
    stage('ContinousBuild')
    {
        sh 'mvn package'
    }
    stage('ContinousDeployment')
    {
        deploy adapters: [tomcat9(credentialsId: 'a0f2d24a-2d01-4a23-9036-b393593f6edb', path: '', url: 'http://172.31.20.135:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('ContinousTesting')
    {
        git 'https://github.com/ANYA-123/FunctionalTesting.git'
        sh 'java -jar /var/lib/jenkins/workspace/ScriptedPipeline?1/testing.jar'
    }
    stage('ContinousDelivery')
    {
        deploy adapters: [tomcat9(credentialsId: 'a0f2d24a-2d01-4a23-9036-b393593f6edb', path: '', url: 'http://172.31.16.238:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
}
