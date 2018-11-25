# wildfly14adoptopenjdk8
Wildfly 14 on adopt openjdk 8

Image uses AdoptOpenJDK 8 (8u172) installed on ubuntu as a first layer. 
https://github.com/AdoptOpenJDK/openjdk-docker/blob/master/8/jdk/ubuntu/Dockerfile.hotspot.releases.full

Next layer installs Wildfly 14, necessary drivers (postgres driver) and sets jboss as an user instead of root.

Recommended way to use this image is to build your application in to next layer using own docker image like this:

FROM dryseawind/wildfly14jdk8

ADD ./deployments /opt/jboss/wildfly-14.0.1.Final/standalone/deployments (for deploying your war)

CMD ["/opt/jboss/wildfly-14.0.1.Final/bin/standalone.sh", "-c", "standalone-ee8.xml", "-b", "0.0.0.0", "-bmanagement", "0.0.0.0" , "--debug"]

Docker hub: https://hub.docker.com/r/dryseawind/wildfly14jdk8/
