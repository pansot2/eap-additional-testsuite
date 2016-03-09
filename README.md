# EAP ADDITIONAL TESTSUITE
============================
An additional JBOSS testsuite in order to facilitate QE.

Write your tests and run them on both EAP and WILDFLY application server.



In order to synchronize the dependecny versions of eap-additional-testsuite with the component versions of the equivalent server you can run the additional-testsuite using -Dstandalone or -Dserver-integration property.

Standalone Mode
---------------
If you enable standalone mode (-Dstandalone), please make sure that the server parent pom is available locally or remotely as an artifact.

Server-Integration Mode
---------------
If you enable server-integration mode (-Dserver-integration), please make sure that the server BOM is available locally or remotely as an artifact.



Testing EAP
-----------
1. Make sure that JBOSS_FOLDER environment variable is set with the path to your JBOSS EAP directory.
2. Make sure that JBOSS_VERSION environment variable is set with the version of JBOSS EAP Server.
3. Build and run the additional testsuite activating the EAP profile (-Deap).


Testing Wildfly
---------------
1. Make sure that JBOSS_FOLDER environment variable is set with the path to your WILDFLY directory.
2. Make sure that JBOSS_VERSION environment variable is set with the version of WILDFLY Server.
3. Build and run the additional testsuite activating the WILDFLY profile (-Dwildfly).


Testing EAP or Wildfly with specific JDK version
------------------------------------------------
1. Make sure that JBOSS_FOLDER is set with the path to your EAP OR WILDFLY directory.
2. Make sure that JBOSS_VERSION environment variable is set with the version of JBOSS EAP OR WILDFLY Server.
3. Make sure that JAVA_HOME is pointing to the jdk of desired version.
4. Build and run the additional testsuite activating the EAP or WILDFLY specific jdk version profile (-Deap-jdk8, -Dwildfly-jdk8).


ADVANTAGES 
----------
1. Having all the tests at one place.
2. Comparison of the servers based on the testsuite.
3. Guarding against regression.

 
MOTIVATION
----------
If a test is developed for server X then it can be automatically tested against all the other servers.

 
HOW TO DEBUG
------------
1. Start the server (that you have defined in JBOSS_FOLDER) with the --debug 'port' option.
2. Connect the Debugger to the Remote VM inside the server using some IDE.
3. Activate the equivalent debug profile at your IDE (eg eap7.testsuite)
4. Set your breakpoints.
5. And then start the debugging executing the specific test which is errorous.


HOW TO BUILD EAP ADDITIONAL TESTSUITE INSIDE AN IDE
--------------------------------------------------
1. Load the project at your IDE.
2. Go to the configuration of the project and activate the profile of the server that you would like (eg eap7.testsuite profile)
3. Go to the properties of the project and add the JBOSS_FOLDER and JBOSS_VERSION environment variables. Also when building the project make sure that the standalone profile is also enabled in parallel with the server profile.
4. Make sure that the server parent pom is available locally or remotely as an artifact.
5. Build your project.


EAP-ADDITIONAL-TESTSUITE INTEGRATED INSIDE THE SERVERS (HOW TO USE)  - AVAILABLE SOON
-------------------------------------------------------------------------------------
1. Send your PR containing the test to eap-additional-testsuite.
2. Before sending the server PR inform the server that you would like to include a specific PR of eap-additional-testsuite, adding the following lines in git-sub-modules/git-sub-module.sh : 
    - git submodule update --init --remote
    - cd ../testsuite/addtional-testsuite/eap-additional-testsuite/
    - git fetch origin refs/pull/8/head && git checkout FETCH_HEAD (declare that you would like to include PR 8 of eap-additional-testsuite)
3. Commit the changes on the server and send the server PR.
4. The specific PR of the test will be tested along with the server PR.

 
OTHER FEATURES
--------------
1. Eap-Additional-Testsuite could be a very helpful tool in combination with the documentation. In parallel with the documentation, examples of use cases could be provided, which could be tested against all the servers.
2. Eap-Additional-Testsuite is the first component to change the relation of Component -> Server to Component <-> Server, as this component can be considered as a part of a Server, but also a Server can be considered as a part of Eap-Additional-Testsuite.

 

EAP-ADDITIONAL-TESTSUITE as a COLLABORATION PROJECT
---------------------------------------------------
Many thanks to Carlo de Wolf for his ideas and help.


#License 
* [GNU Lesser General Public License Version 2.1](http://www.gnu.org/licenses/lgpl-2.1-standalone.html)

