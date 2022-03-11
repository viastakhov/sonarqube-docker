# Starting SonarQube, and using Sonar Scanner

### Starting SonarQub:
```bash
docker-compose up -d
```

### Open SonarQube in browser at http://localhost:9000/
* Login: admin
* Password: admin

### Open security page and generate a token at http://localhost:9000/account/security/

### Clone git repo (java projects)
```bash
git clone https://github.com/SonarSource/sonar-scanning-examples.git
```

### Generate Jacoco report
```bash
cd sonar-scanning-examples\sonarqube-scanner-maven\maven-basic
mvn clean verify
```

### Install Sonar scanner
* Download scanner from https://docs.sonarqube.org/latest/analysis/scan/sonarscanner/
* Setup scanner like this one:
```
#Configure here general information about the environment, such as SonarQube server connection details for example
#No information about specific project should appear here

#----- Default SonarQube server
sonar.host.url=http://localhost:9000

#----- Default source code encoding
sonar.sourceEncoding=UTF-8

sonar.login=<Your generated token in SonarQube>
sonar.projectKey=<project key>
sonar.projectName=<project name>
sonar.coverage.jacoco.xmlReportPaths=./sonar-scanning-examples/sonarqube-scanner-maven/maven-basic/target/site/jacoco/jacoco.xml
sonar.scm.provider=git
sonar.projectBaseDir=./sonar-scanning-examples
sonar.sources=./sonarqube-scanner-maven/maven-basic/src
sonar.coverage.exclusions=**/src/test/**/*.java
sonar.java.binaries=./sonarqube-scanner-maven/maven-basic/target/classes
sonar.java.test.binaries=./sonarqube-scanner-maven/maven-basic/target/test-classes
sonar.java.libraries=./sonarqube-scanner-maven/maven-basic/target
```

### Run Sonar scanner
```bash
cd sonar-scanner-4.7.0.2747-windows\bin
sh sonar-scanner
```

### Check new project in SonarQube

### Shutdown down the containers, network, and volumes
```bash
docker-compose down -v
```

References:
* https://www.cprime.com/resources/blog/running-sonarqube
* https://community.sonarsource.com/t/sonarqube-docker-container-is-getting-restarted/47842
* https://community.sonarsource.com/t/could-not-find-java-in-es-java-home-at-usr-bin-java/56693/2
* https://docs.sonarqube.org/latest/analysis/languages/java
* https://docs.sonarqube.org/latest/analysis/scan/sonarscanner-for-maven/
* https://docs.sonarqube.org/latest/analysis/scan/sonarscanner/
* https://github.com/SonarSource/sonar-scanning-examples
* https://www.jacoco.org/jacoco/index.html
