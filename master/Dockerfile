FROM node as nodejs

FROM jenkins/jenkins:2.222.4

LABEL maintainer="ewe@praqma.net"
COPY plugins_extra.txt /usr/share/jenkins/ref/plugins_extra.txt
COPY --from=nodejs /usr/local/bin/node /usr/local/bin/node

ENV JENKINS_HOME /var/jenkins_home

ARG JAVA_OPTS
ENV JAVA_OPTS "-Djenkins.install.runSetupWizard=false ${JAVA_OPTS:-}"

RUN xargs /usr/local/bin/install-plugins.sh < /usr/share/jenkins/ref/plugins_extra.txt
