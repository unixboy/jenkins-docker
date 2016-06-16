# docker-jenkins-centos-base

Centos base image for a jenkins build node

## Branch strategy

- master - not used
- Each branch then IDs which centos version it is for (ie. centos6, centos7).  DockerHub is then configured to autobuild these branches and label the containers accordingly.  Generally, it's only the Dockerfile changing with the branch but any changes to common scripts can then be merged to all branches as needed.

This starts with a base centos image and then adds the packages listed in the yum-packages.list file.  In addition, it installs:

- the EPEL repository
- the rpmforge repository
- pip
- the AWS CLI

We also create the bldmgr user (note the userID - this must match across all nodes) and setup SSHD.  SSHD is only used if this node is being launched by the Jenkins docker plugin on-the-fly.

