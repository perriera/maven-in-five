
# maven-in-five

[Maven in 5 Minutes](https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html)

### Prerequisites[](https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html#prerequisites)

You must understand how to install software on your computer. If you do not know how to do this, please ask someone at your office, school, etc. or pay someone to explain this to you. The Maven mailing lists are not the best place to ask for this advice.

### Installation
**Java Installation** on Ubuntu
```undefined
sudo apt install openjdk-8-jre openjdk-8-jdk
```
[How to set JAVA_HOME for Java?](https://askubuntu.com/questions/175514/how-to-set-java-home-for-java)

**Maven Installation** on Ubuntu
[How to Install Apache Maven on Ubuntu 20.04](https://linuxize.com/post/how-to-install-apache-maven-on-ubuntu-20-04/)
[Maven Tutorial](http://tutorials.jenkov.com/maven/maven-tutorial.html#installing-maven)

_Maven is a Java tool, so you must have  [Java](https://www.oracle.com/technetwork/java/javase/downloads/index.html)  installed in order to proceed._

First,  [download Maven](https://maven.apache.org/download.html)  and follow the  [installation instructions](https://maven.apache.org/install.html). After that, type the following in a terminal or in a command prompt:

	mvn --version

It should print out your installed version of Maven, for example:

### Running Maven Tools[](https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html#running-maven-tools)

#### Maven Phases[](https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html#maven-phases)

Although hardly a comprehensive list, these are the most common  _default_  lifecycle phases executed.

-   **validate**: validate the project is correct and all necessary information is available
-   **compile**: compile the source code of the project
-   **test**: test the compiled source code using a suitable unit testing framework. These tests should not require the code be packaged or deployed
-   **package**: take the compiled code and package it in its distributable format, such as a JAR.
-   **integration-test**: process and deploy the package if necessary into an environment where integration tests can be run
-   **verify**: run any checks to verify the package is valid and meets quality criteria
-   **install**: install the package into the local repository, for use as a dependency in other projects locally
-   **deploy**: done in an integration or release environment, copies the final package to the remote repository for sharing with other developers and projects.

There are two other Maven lifecycles of note beyond the  _default_  list above. They are

-   **clean**: cleans up artifacts created by prior builds

-   **site**: generates site documentation for this project
#### Build the Project[](https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html#build-the-project)

	mvn package

The command line will print out various actions, and end with the following:

	 ...
	[INFO] ---------------------------------------------------------------
	[INFO] BUILD SUCCESS
	[INFO] ---------------------------------------------------------------
	[INFO] Total time:  2.953 s
	[INFO] Finished at: 2019-11-24T13:05:10+01:00
	[INFO] ---------------------------------------------------------------

Unlike the first command executed (_archetype:generate_), the second is simply a single word -  _package_. Rather than a  _goal_, this is a  _phase_. A phase is a step in the  [build lifecycle](https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html), which is an ordered sequence of phases. When a phase is given, Maven executes every phase in the sequence up to and including the one defined. For example, if you execute the  _compile_  phase, the phases that actually get executed are:

1.  validate
2.  generate-sources
3.  process-sources
4.  generate-resources
5.  process-resources
6.  compile

You may test the newly compiled and packaged JAR with the following command:

	java -cp target/my-app-1.0-SNAPSHOT.jar com.mycompany.app.App

Which will print the quintessential:

	Hello World!

Phases are actually mapped to underlying goals. The specific goals executed per phase is dependant upon the packaging type of the project. For example,  _package_  executes  _jar:jar_  if the project type is a JAR, and  _war:war_  if the project type is - you guessed it - a WAR.

An interesting thing to note is that phases and goals may be executed in sequence.

	mvn clean dependency:copy-dependencies package

This command will clean the project, copy dependencies, and package the project (executing all phases up to  _package_, of course).

#### Generating the Site[](https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html#generating-the-site)

	mvn site
This phase generates a site based upon information on the project's pom. You can look at the documentation generated under  `target/site`.

### Conclusion[](https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html#conclusion)

We hope this quick overview has piqued your interest in the versatility of Maven. Note that this is a very truncated quick-start guide. Now you are ready for more comprehensive details concerning the actions you have just performed. Check out the  [Maven Getting Started Guide](https://maven.apache.org/guides/getting-started/index.html).
