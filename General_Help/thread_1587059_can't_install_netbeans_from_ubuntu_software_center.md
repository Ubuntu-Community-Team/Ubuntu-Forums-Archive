---
title: "can't install netbeans from ubuntu software center"
date: 2010-10-02
forum: General Help
---

### Post by searayman on 2010-10-02
When I try and install netbeans from ubuntu software center on latest version of ubuntu I get this error:

requires installation of untrusted packages:

The action would require the installation of packages from not authenticated sources.

then under details it says this:

ca-certificates-java default-jdk default-jdk-doc default-jre default-jre-headless gcj-4.4-base gcj-4.4-jre-lib java-common javahelp2 jetty jruby1.1 jsvc junit junit4 libaccess-bridge-java libaccess-bridge-java-jni libappframework-java libasm2-java libbeansbinding-java libcobertura-java libcommons-beanutils-java libcommons-collections3-java libcommons-compress-java libcommons-daemon-java libcommons-digester-java libcommons-logging-java libcommons-net-java libdb-je-java libdb4.7-java libdb4.7-java-gcj libfreemarker-java libgcj-bc libgcj-common libgcj10 libhamcrest-java libice-dev libicu4j-java libini4j-java libjaxp1.3-java libjetty-java libjetty-java-doc libjline-java libjna-java libjsch-java libjtidy-java libjzlib-java liblog4j1.2-java liblucene2-java libnb-apisupport1-java libnb-ide12-java libnb-java3-java libnb-javaparser-java libnb-platform-devel-java libnb-platform11-java libnb-svnclientadapter-java liboro-java libpthread-stubs0 libpthread-stubs0-dev libregexp-java libservlet2.3-java libservlet2.4-java libslf4j-java libsm-dev libsvn-java libswing-layout-java libswingworker-java libswingx-java libx11-dev libxau-dev libxcb1-dev libxdmcp-dev libxerces2-java libxml-commons-resolver1.1-java libxt-dev netbeans tzdata-java x11proto-core-dev x11proto-input-dev x11proto-kb-dev xtrans-dev


any help to install this would be great as i need it to complete some home work

---

### Post by searayman on 2010-10-02
anyone?

---

### Post by lykeion on 2010-10-03
Not so familiar with NetBeans since I don't particulary like this IDE. But my guess is you need to install Sun Java JDK.
1. Close Ubuntu Software Center
2. Open a terminal (Applications > Accessories > Terminal) and enter these commands:```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
sudo apt-get update
sudo apt-get install sun-java6-jdk
sudo apt-get install netbeans
```

---

