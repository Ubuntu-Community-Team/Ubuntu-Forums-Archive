---
title: "Not able to add packages."
date: 2011-03-26
forum: General Help
---

### Post by novice_coder on 2011-03-26
[B]When I try to add a new new package (such as sun-java6-jre or sun-java6-jdk) using 'Synaptic Package Manager', I can see no activity going on and upon canceling it, I get the following response.

[I]W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libp/libpthread-stubs/libpthread-stubs0-dev_0.1-2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libp/libpthread-stubs/libpthread-stubs0-dev_0.1-2_i386.deb)
  
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb1-dev_1.1.93-0ubuntu3.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb1-dev_1.1.93-0ubuntu3.1_i386.deb)
[/I]
Could anyone help me figure out what is wrong and what steps I should be taking to rectify it.[/B] :confused:

In case more information is required, please see the results of the same procedure done using the terminal.

$ sudo apt-get install sun-java6-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ant ant-gcj ant-optional ant-optional-gcj apache2-utils gcj-4.3-base
  gsfonts-x11 icedtea-6-jre-cacao icedtea6-plugin javahelp2 jetty junit junit4
  libappframework-java libapr1 libaprutil1 libbcel-java libbeansbinding-java
  libcommons-beanutils-java libcommons-collections-java
  libcommons-collections3-java libcommons-dbcp-java libcommons-digester-java
  libcommons-el-java libcommons-launcher-java libcommons-logging-java
  libcommons-modeler-java libcommons-net-java libcommons-pool-java
  libdb-je-java libdb4.6-java libdb4.6-java-gcj libecj-java libecj-java-gcj
  libfreemarker-java libgcj-bc libgcj-common libgcj9-0 libgcj9-jar
  libini4j-java libjaxp1.3-java libjaxp1.3-java-gcj libjline-java libjna-java
  libjsch-java libjtidy-java liblog4j1.2-java liblog4j1.2-java-gcj
  liblucene2-java libmx4j-java libnb-apisupport1-java libnb-ide10-java
  libnb-java2-java libnb-javaparser-java libnb-platform-devel-java
  libnb-platform9-java libnb-svnclientadapter-java libneon27-gnutls
  libnspr4-0d libnss3-1d liboro-java libpq5 libpthread-stubs0-dev
  libregexp-java libservlet2.3-java libssl0.9.8 libsvn-java libsvn1
  libswing-layout-java libswingworker-java libtomcat5.5-java libx11-dev
  libxcb1-dev libxerces2-java libxerces2-java-gcj
  libxml-commons-resolver1.1-java libxt-dev odbcinst1debian1 openjdk-6-jdk
  openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib subversion
  sun-java6-bin sun-java6-jre unixodbc visualvm xulrunner-1.9.2
Suggested packages:
  ant-doc libbsf-java libxalan2-java jython antlr libjdepend-java
  libgnumail-java javacc javahelp2-doc libapache2-mod-jk junit-doc
  libappframework-java-doc libbcel-java-doc libswingworker-java-doc
  libcommons-beanutils-java-doc libcommons-collections3-java-doc
  libcommons-digester-java-doc liblogkit-java libavalon-framework-java
  libcommons-logging-java-doc classpath-doc ecj libgcj9-dbg libgcj9-0-awt
  libjline-java-doc libjna-java-doc libjtidy-java-doc libnb-platform9-java-doc
  libswing-layout-java-doc tomcat5.5 libxerces2-java-doc
  libxml-commons-resolver1.1-java-doc openjdk-6-demo openjdk-6-source
  sun-java6-fonts subversion-tools db4.6-util patch sun-java6-demo
  openjdk-6-doc sun-java6-source sun-java6-plugin ia32-sun-java6-plugin
  libmyodbc odbc-postgresql libct1
Recommended packages:
  default-jdk java-compiler java-sdk
The following NEW packages will be installed:
  ant ant-gcj ant-optional ant-optional-gcj apache2-utils gcj-4.3-base
  gsfonts-x11 javahelp2 jetty junit junit4 libappframework-java libapr1
  libaprutil1 libbcel-java libbeansbinding-java libcommons-beanutils-java
  libcommons-collections-java libcommons-collections3-java
  libcommons-dbcp-java libcommons-digester-java libcommons-el-java
  libcommons-launcher-java libcommons-logging-java libcommons-modeler-java
  libcommons-net-java libcommons-pool-java libdb-je-java libdb4.6-java
  libdb4.6-java-gcj libecj-java libecj-java-gcj libfreemarker-java libgcj-bc
  libgcj-common libgcj9-0 libgcj9-jar libini4j-java libjaxp1.3-java
  libjaxp1.3-java-gcj libjline-java libjna-java libjsch-java libjtidy-java
  liblog4j1.2-java liblog4j1.2-java-gcj liblucene2-java libmx4j-java
  libnb-apisupport1-java libnb-ide10-java libnb-java2-java
  libnb-javaparser-java libnb-platform-devel-java libnb-platform9-java
  libnb-svnclientadapter-java libneon27-gnutls liboro-java libpq5
  libpthread-stubs0-dev libregexp-java libservlet2.3-java libsvn-java libsvn1
  libswing-layout-java libswingworker-java libtomcat5.5-java libx11-dev
  libxcb1-dev libxerces2-java libxerces2-java-gcj
  libxml-commons-resolver1.1-java libxt-dev odbcinst1debian1 openjdk-6-jdk
  subversion sun-java6-bin sun-java6-jdk sun-java6-jre unixodbc visualvm
  xulrunner-1.9.2
The following packages will be upgraded:
  icedtea-6-jre-cacao icedtea6-plugin libnspr4-0d libnss3-1d libssl0.9.8
  openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib
8 upgraded, 81 newly installed, 0 to remove and 319 not upgraded.
Need to get 192MB of archives.
After this operation, 441MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main libpthread-stubs0-dev 0.1-2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/main libxcb1-dev 1.1.93-0ubuntu3.1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main libx11-dev 2:1.1.99.2-1ubuntu2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main libxt-dev 1:1.0.5-3ubuntu1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/multiverse sun-java6-jre 6.22-0ubuntu1~9.04.1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main odbcinst1debian1 2.2.11-16build3
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main unixodbc 2.2.11-16build3
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main libjaxp1.3-java 1.3.04-3ubuntu2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main libxerces2-java 2.9.1-2ubuntu2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main libgcj-common 1:4.3.3-1ubuntu1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main gcj-4.3-base 4.3.3-5ubuntu4
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main libgcj9-0 4.3.3-5ubuntu4
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main libgcj-bc 4.3.3-1ubuntu1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main gsfonts-x11 0.21
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe javahelp2 2.0.05-3
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main liblog4j1.2-java 1.2.15-4
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main libregexp-java 1.4-5ubuntu1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main libbcel-java 5.2-3ubuntu3
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main libmx4j-java 3.0.2-4
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main libecj-java 3.4.2-0ubuntu1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe libcommons-el-java 1.0-4
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main libcommons-collections-java 2.1.1-8ubuntu1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main libservlet2.3-java 4.0-10ubuntu3
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main libcommons-logging-java 1.1.1-2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe libcommons-launcher-java 1.1-3ubuntu1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main libcommons-collections3-java 3.2.1-1ubuntu2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main libcommons-beanutils-java 1.8.0~beta-1ubuntu1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe libcommons-digester-java 1.8-2ubuntu1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe libcommons-modeler-java 2.0.1-4
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main libcommons-pool-java 1.4-0ubuntu1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main libcommons-dbcp-java 1.2.2-1ubuntu1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe libtomcat5.5-java 5.5.26-5ubuntu1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe jetty 5.1.14-1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main junit 3.8.2-1ubuntu2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe junit4 4.3.1-4
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe libswingworker-java 1.1-0ubuntu3
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe libappframework-java 1.03-0ubuntu3
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe libbeansbinding-java 1.2.1-0ubuntu3
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main liboro-java 2.0.8a-4ubuntu2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main libcommons-net-java 1.4.1-1ubuntu2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe libdb-je-java 3.3.62-2ubuntu1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main libdb4.6-java 4.6.21-12
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main libdb4.6-java-gcj 4.6.21-12
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main libecj-java-gcj 3.4.2-0ubuntu1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe libfreemarker-java 2.3.13+debian1-1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main libgcj9-jar 4.3.3-5ubuntu4
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe libini4j-java 0.2.6-0ubuntu3
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main libjaxp1.3-java-gcj 1.3.04-3ubuntu2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main libjline-java 0.9.94-1ubuntu1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe libjna-java 3.0.4-0ubuntu2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main libjsch-java 0.1.37-3ubuntu2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe libjtidy-java 7+svn20070309-2ubuntu2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main liblog4j1.2-java-gcj 1.2.15-4
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe liblucene2-java 2.4.0+ds1-5ubuntu1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe libswing-layout-java 1.0.3-1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe libnb-platform9-java 6.5-0ubuntu2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe libnb-platform-devel-java 6.5-0ubuntu2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main libxml-commons-resolver1.1-java 1.2-4
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe libnb-svnclientadapter-java 6.5-0ubuntu1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/universe libnb-ide10-java 6.5-0ubuntu2.1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe libnb-javaparser-java 6.5-0ubuntu1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/universe libnb-java2-java 6.5-0ubuntu2.1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/universe libnb-apisupport1-java 6.5-0ubuntu2.1
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main libxerces2-java-gcj 2.9.1-2ubuntu2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/universe visualvm 0.20080728-1ubuntu2
  Could not resolve 'in.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse sun-java6-jre 6.22-0ubuntu1~9.04.1
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse sun-java6-bin 6.22-0ubuntu1~9.04.1
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse sun-java6-jdk 6.22-0ubuntu1~9.04.1
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main libssl0.9.8 0.9.8g-15ubuntu3.6
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main icedtea-6-jre-cacao 6b18-1.8.2-4ubuntu1~9.04.1
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main openjdk-6-jre-lib 6b18-1.8.2-4ubuntu1~9.04.1
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main openjdk-6-jre 6b18-1.8.2-4ubuntu1~9.04.1
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main openjdk-6-jre-headless 6b18-1.8.2-4ubuntu1~9.04.1
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main icedtea6-plugin 6b18-1.8.2-4ubuntu1~9.04.1
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main libnspr4-0d 4.8.6-0ubuntu0.9.04.1
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main libnss3-1d 3.12.8-0ubuntu0.9.04.1
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main xulrunner-1.9.2 1.9.2.11+build3+nobinonly-0ubuntu0.9.04.1
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main ant 1.7.1-0ubuntu2.2
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main ant-gcj 1.7.1-0ubuntu2.2
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main ant-optional 1.7.1-0ubuntu2.2
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main ant-optional-gcj 1.7.1-0ubuntu2.2
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main libapr1 1.2.12-5ubuntu0.1
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main libpq5 8.3.12-0ubuntu9.04
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main libaprutil1 1.2.12+dfsg-8ubuntu0.3
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main apache2-utils 2.2.11-2ubuntu2.7
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main libneon27-gnutls 0.28.2-6.1ubuntu0.1
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main libsvn1 1.5.4dfsg1-1ubuntu2.1
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main subversion 1.5.4dfsg1-1ubuntu2.1
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe libsvn-java 1.5.4dfsg1-1ubuntu2.1
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main openjdk-6-jdk 6b18-1.8.2-4ubuntu1~9.04.1
  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libp/libpthread-stubs/libpthread-stubs0-dev_0.1-2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libp/libpthread-stubs/libpthread-stubs0-dev_0.1-2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb1-dev_1.1.93-0ubuntu3.1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb1-dev_1.1.93-0ubuntu3.1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libx11/libx11-dev_1.1.99.2-1ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libx11/libx11-dev_1.1.99.2-1ubuntu2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxt/libxt-dev_1.0.5-3ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxt/libxt-dev_1.0.5-3ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jre_6.22-0ubuntu1~9.04.1_all.deb]("http://security.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jre_6.22-0ubuntu1%7E9.04.1_all.deb")  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/u/unixodbc/odbcinst1debian1_2.2.11-16build3_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/u/unixodbc/odbcinst1debian1_2.2.11-16build3_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/u/unixodbc/unixodbc_2.2.11-16build3_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/u/unixodbc/unixodbc_2.2.11-16build3_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6.22-0ubuntu1~9.04.1_i386.deb]("http://security.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6.22-0ubuntu1%7E9.04.1_i386.deb")  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jdk_6.22-0ubuntu1~9.04.1_i386.deb]("http://security.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jdk_6.22-0ubuntu1%7E9.04.1_i386.deb")  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8g-15ubuntu3.6_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8g-15ubuntu3.6_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/icedtea-6-jre-cacao_6b18-1.8.2-4ubuntu1~9.04.1_i386.deb]("http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/icedtea-6-jre-cacao_6b18-1.8.2-4ubuntu1%7E9.04.1_i386.deb")  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre-lib_6b18-1.8.2-4ubuntu1~9.04.1_all.deb]("http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre-lib_6b18-1.8.2-4ubuntu1%7E9.04.1_all.deb")  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre_6b18-1.8.2-4ubuntu1~9.04.1_i386.deb]("http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre_6b18-1.8.2-4ubuntu1%7E9.04.1_i386.deb")  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre-headless_6b18-1.8.2-4ubuntu1~9.04.1_i386.deb]("http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre-headless_6b18-1.8.2-4ubuntu1%7E9.04.1_i386.deb")  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/icedtea6-plugin_6b18-1.8.2-4ubuntu1~9.04.1_i386.deb]("http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/icedtea6-plugin_6b18-1.8.2-4ubuntu1%7E9.04.1_i386.deb")  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/nspr/libnspr4-0d_4.8.6-0ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/nspr/libnspr4-0d_4.8.6-0ubuntu0.9.04.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.12.8-0ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.12.8-0ubuntu0.9.04.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.2/xulrunner-1.9.2_1.9.2.11+build3+nobinonly-0ubuntu0.9.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.2/xulrunner-1.9.2_1.9.2.11+build3+nobinonly-0ubuntu0.9.04.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libj/libjaxp1.3-java/libjaxp1.3-java_1.3.04-3ubuntu2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libj/libjaxp1.3-java/libjaxp1.3-java_1.3.04-3ubuntu2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxerces2-java/libxerces2-java_2.9.1-2ubuntu2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxerces2-java/libxerces2-java_2.9.1-2ubuntu2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/ant/ant_1.7.1-0ubuntu2.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/a/ant/ant_1.7.1-0ubuntu2.2_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/libgcj-common_4.3.3-1ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/libgcj-common_4.3.3-1ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/gcj-4.3/gcj-4.3-base_4.3.3-5ubuntu4_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/gcj-4.3/gcj-4.3-base_4.3.3-5ubuntu4_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/gcj-4.3/libgcj9-0_4.3.3-5ubuntu4_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/gcj-4.3/libgcj9-0_4.3.3-5ubuntu4_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/libgcj-bc_4.3.3-1ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/libgcj-bc_4.3.3-1ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/ant/ant-gcj_1.7.1-0ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/ant/ant-gcj_1.7.1-0ubuntu2.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/ant/ant-optional_1.7.1-0ubuntu2.2_all.deb](http://security.ubuntu.com/ubuntu/pool/main/a/ant/ant-optional_1.7.1-0ubuntu2.2_all.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/ant/ant-optional-gcj_1.7.1-0ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/ant/ant-optional-gcj_1.7.1-0ubuntu2.2_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apr/libapr1_1.2.12-5ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apr/libapr1_1.2.12-5ubuntu0.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.3/libpq5_8.3.12-0ubuntu9.04_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.3/libpq5_8.3.12-0ubuntu9.04_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apr-util/libaprutil1_1.2.12+dfsg-8ubuntu0.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apr-util/libaprutil1_1.2.12+dfsg-8ubuntu0.3_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-utils_2.2.11-2ubuntu2.7_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-utils_2.2.11-2ubuntu2.7_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/gsfonts-x11/gsfonts-x11_0.21_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/gsfonts-x11/gsfonts-x11_0.21_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/j/javahelp2/javahelp2_2.0.05-3_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/j/javahelp2/javahelp2_2.0.05-3_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/j/jakarta-log4j/liblog4j1.2-java_1.2.15-4_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/j/jakarta-log4j/liblog4j1.2-java_1.2.15-4_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libr/libregexp-java/libregexp-java_1.4-5ubuntu1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libr/libregexp-java/libregexp-java_1.4-5ubuntu1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/b/bcel/libbcel-java_5.2-3ubuntu3_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/b/bcel/libbcel-java_5.2-3ubuntu3_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libm/libmx4j-java/libmx4j-java_3.0.2-4_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libm/libmx4j-java/libmx4j-java_3.0.2-4_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/e/ecj/libecj-java_3.4.2-0ubuntu1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/e/ecj/libecj-java_3.4.2-0ubuntu1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/libc/libcommons-el-java/libcommons-el-java_1.0-4_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/libc/libcommons-el-java/libcommons-el-java_1.0-4_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libc/libcommons-collections-java/libcommons-collections-java_2.1.1-8ubuntu1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libc/libcommons-collections-java/libcommons-collections-java_2.1.1-8ubuntu1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/j/javax-servletapi2.3/libservlet2.3-java_4.0-10ubuntu3_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/j/javax-servletapi2.3/libservlet2.3-java_4.0-10ubuntu3_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libc/libcommons-logging-java/libcommons-logging-java_1.1.1-2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libc/libcommons-logging-java/libcommons-logging-java_1.1.1-2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/libc/libcommons-launcher-java/libcommons-launcher-java_1.1-3ubuntu1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/libc/libcommons-launcher-java/libcommons-launcher-java_1.1-3ubuntu1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libc/libcommons-collections3-java/libcommons-collections3-java_3.2.1-1ubuntu2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libc/libcommons-collections3-java/libcommons-collections3-java_3.2.1-1ubuntu2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/c/commons-beanutils/libcommons-beanutils-java_1.8.0~beta-1ubuntu1_all.deb]("http://in.archive.ubuntu.com/ubuntu/pool/main/c/commons-beanutils/libcommons-beanutils-java_1.8.0%7Ebeta-1ubuntu1_all.deb")  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/libc/libcommons-digester-java/libcommons-digester-java_1.8-2ubuntu1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/libc/libcommons-digester-java/libcommons-digester-java_1.8-2ubuntu1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/libc/libcommons-modeler-java/libcommons-modeler-java_2.0.1-4_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/libc/libcommons-modeler-java/libcommons-modeler-java_2.0.1-4_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/c/commons-pool/libcommons-pool-java_1.4-0ubuntu1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/c/commons-pool/libcommons-pool-java_1.4-0ubuntu1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libc/libcommons-dbcp-java/libcommons-dbcp-java_1.2.2-1ubuntu1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libc/libcommons-dbcp-java/libcommons-dbcp-java_1.2.2-1ubuntu1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/t/tomcat5.5/libtomcat5.5-java_5.5.26-5ubuntu1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/t/tomcat5.5/libtomcat5.5-java_5.5.26-5ubuntu1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/j/jetty/jetty_5.1.14-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/j/jetty/jetty_5.1.14-1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/j/junit/junit_3.8.2-1ubuntu2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/j/junit/junit_3.8.2-1ubuntu2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/j/junit4/junit4_4.3.1-4_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/j/junit4/junit4_4.3.1-4_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/libs/libswingworker-java/libswingworker-java_1.1-0ubuntu3_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/libs/libswingworker-java/libswingworker-java_1.1-0ubuntu3_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/liba/libappframework-java/libappframework-java_1.03-0ubuntu3_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/liba/libappframework-java/libappframework-java_1.03-0ubuntu3_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/libb/libbeansbinding-java/libbeansbinding-java_1.2.1-0ubuntu3_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/libb/libbeansbinding-java/libbeansbinding-java_1.2.1-0ubuntu3_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libo/liboro-java/liboro-java_2.0.8a-4ubuntu2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libo/liboro-java/liboro-java_2.0.8a-4ubuntu2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libc/libcommons-net-java/libcommons-net-java_1.4.1-1ubuntu2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libc/libcommons-net-java/libcommons-net-java_1.4.1-1ubuntu2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/libd/libdb-je-java/libdb-je-java_3.3.62-2ubuntu1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/libd/libdb-je-java/libdb-je-java_3.3.62-2ubuntu1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/d/db4.6/libdb4.6-java_4.6.21-12_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/d/db4.6/libdb4.6-java_4.6.21-12_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/d/db4.6/libdb4.6-java-gcj_4.6.21-12_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/d/db4.6/libdb4.6-java-gcj_4.6.21-12_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/e/ecj/libecj-java-gcj_3.4.2-0ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/e/ecj/libecj-java-gcj_3.4.2-0ubuntu1_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/libf/libfreemarker-java/libfreemarker-java_2.3.13+debian1-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/libf/libfreemarker-java/libfreemarker-java_2.3.13+debian1-1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/gcj-4.3/libgcj9-jar_4.3.3-5ubuntu4_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/gcj-4.3/libgcj9-jar_4.3.3-5ubuntu4_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/libi/libini4j-java/libini4j-java_0.2.6-0ubuntu3_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/libi/libini4j-java/libini4j-java_0.2.6-0ubuntu3_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libj/libjaxp1.3-java/libjaxp1.3-java-gcj_1.3.04-3ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libj/libjaxp1.3-java/libjaxp1.3-java-gcj_1.3.04-3ubuntu2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/j/jline/libjline-java_0.9.94-1ubuntu1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/j/jline/libjline-java_0.9.94-1ubuntu1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/libj/libjna-java/libjna-java_3.0.4-0ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/libj/libjna-java/libjna-java_3.0.4-0ubuntu2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/j/jsch/libjsch-java_0.1.37-3ubuntu2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/j/jsch/libjsch-java_0.1.37-3ubuntu2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/j/jtidy/libjtidy-java_7+svn20070309-2ubuntu2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/j/jtidy/libjtidy-java_7+svn20070309-2ubuntu2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/j/jakarta-log4j/liblog4j1.2-java-gcj_1.2.15-4_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/j/jakarta-log4j/liblog4j1.2-java-gcj_1.2.15-4_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/l/lucene2/liblucene2-java_2.4.0+ds1-5ubuntu1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/l/lucene2/liblucene2-java_2.4.0+ds1-5ubuntu1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/s/swing-layout/libswing-layout-java_1.0.3-1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/s/swing-layout/libswing-layout-java_1.0.3-1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/libn/libnb-platform-java/libnb-platform9-java_6.5-0ubuntu2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/libn/libnb-platform-java/libnb-platform9-java_6.5-0ubuntu2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/libn/libnb-platform-java/libnb-platform-devel-java_6.5-0ubuntu2_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/libn/libnb-platform-java/libnb-platform-devel-java_6.5-0ubuntu2_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxml-commons-resolver1.1-java/libxml-commons-resolver1.1-java_1.2-4_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxml-commons-resolver1.1-java/libxml-commons-resolver1.1-java_1.2-4_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/neon27/libneon27-gnutls_0.28.2-6.1ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/neon27/libneon27-gnutls_0.28.2-6.1ubuntu0.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/subversion/libsvn1_1.5.4dfsg1-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/subversion/libsvn1_1.5.4dfsg1-1ubuntu2.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/subversion/subversion_1.5.4dfsg1-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/subversion/subversion_1.5.4dfsg1-1ubuntu2.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/s/subversion/libsvn-java_1.5.4dfsg1-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/universe/s/subversion/libsvn-java_1.5.4dfsg1-1ubuntu2.1_i386.deb)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/libn/libnb-svnclientadapter-java/libnb-svnclientadapter-java_6.5-0ubuntu1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/libn/libnb-svnclientadapter-java/libnb-svnclientadapter-java_6.5-0ubuntu1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/n/netbeans/libnb-ide10-java_6.5-0ubuntu2.1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/n/netbeans/libnb-ide10-java_6.5-0ubuntu2.1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/libn/libnb-javaparser-java/libnb-javaparser-java_6.5-0ubuntu1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/libn/libnb-javaparser-java/libnb-javaparser-java_6.5-0ubuntu1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/n/netbeans/libnb-java2-java_6.5-0ubuntu2.1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/n/netbeans/libnb-java2-java_6.5-0ubuntu2.1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/n/netbeans/libnb-apisupport1-java_6.5-0ubuntu2.1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/n/netbeans/libnb-apisupport1-java_6.5-0ubuntu2.1_all.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxerces2-java/libxerces2-java-gcj_2.9.1-2ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/libx/libxerces2-java/libxerces2-java-gcj_2.9.1-2ubuntu2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jdk_6b18-1.8.2-4ubuntu1~9.04.1_i386.deb]("http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jdk_6b18-1.8.2-4ubuntu1%7E9.04.1_i386.deb")  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/v/visualvm/visualvm_0.20080728-1ubuntu2_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/v/visualvm/visualvm_0.20080728-1ubuntu2_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
$

---

### Post by andrewthomas on 2011-03-26
You need to upgrade.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

[https://lists.ubuntu.com/archives/ubuntu-announce/2010-September/000137.html](https://lists.ubuntu.com/archives/ubuntu-announce/2010-September/000137.html)

---

### Post by Old_Grey_Wolf on 2011-03-26
A lot of people are having trouble with the server in India for the past few days. Try a different server.

Go to the menu System > Administration > Synaptic Package Manager.

When the window opens use the menu Settings > Repositories.

When the window opens use the Download From: pull-down to select Other...

Then select a different server or click the "Select Best Server" button.

Then click on the choose server button.

Click on the Reload button on the top left of the Synaptic Package Manager window.

Then try downloading the desktop package again.

---

### Post by Old_Grey_Wolf on 2011-03-27
> **andrewthomas said:**
> You need to upgrade.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

[https://lists.ubuntu.com/archives/ubuntu-announce/2010-September/000137.html](https://lists.ubuntu.com/archives/ubuntu-announce/2010-September/000137.html)

I missed the fact that he is using 9.04. That will not update because it is not supported as you pointed out.

---

### Post by novice_coder on 2011-04-02
Thank you for the replies. I hope upgrading to 10.10 will solve the problem. :)

---

