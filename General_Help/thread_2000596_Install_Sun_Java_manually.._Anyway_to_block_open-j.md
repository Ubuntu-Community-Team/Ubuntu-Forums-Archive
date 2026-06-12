---
title: "Install Sun Java manually.. Anyway to block open-jdk?"
date: 2012-06-09
forum: General Help
---

### Post by rhugga on 2012-06-09
I installed Sun Java 7 manually (using update-alternatives) however any java related component I need to install wants to pull down open-jdk, like ant for example:

# apt-get install ant
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ant-optional ca-certificates-java default-jre-headless icedtea-6-jre-cacao icedtea-6-jre-jamvm libxerces2-java libxml-commons-external-java libxml-commons-resolver1.1-java openjdk-6-jre-headless openjdk-6-jre-lib tzdata-java
Suggested packages:
  default-jdk java-compiler java-sdk ant-gcj ant-doc libbsf-java liboro-java libxalan2-java libjaxp1.3-java junit liblog4j1.2-java libregexp-java jython antlr libbcel-java libcommons-logging-java libjdepend-java libgnumail-java
  libcommons-net-java libjsch-java javacc ant-optional-gcj default-jre libxerces2-java-doc libxerces2-java-gcj libxml-commons-resolver1.1-java-doc sun-java6-fonts fonts-ipafont-gothic fonts-ipafont-mincho ttf-telugu-fonts
  ttf-oriya-fonts ttf-kannada-fonts ttf-bengali-fonts
The following NEW packages will be installed:
  ant ant-optional ca-certificates-java default-jre-headless icedtea-6-jre-cacao icedtea-6-jre-jamvm libxerces2-java libxml-commons-external-java libxml-commons-resolver1.1-java openjdk-6-jre-headless openjdk-6-jre-lib tzdata-java
0 upgraded, 12 newly installed, 0 to remove and 0 not upgraded.
Need to get 38.4 MB of archives.
After this operation, 97.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? n

Grr... this is what is always so frustrating about ubuntu..

---

### Post by Cheesemill on 2012-06-09
I'm not sure how to solve your exact problem but installing Oracle Java from the WebUpd8 team PPA instead of manually will let you install applications that depend on Java without pulling in any of the Open Java packages (as well as staying up to date).
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

Because you have installed manually Ubuntu doesn't recognise that you have Java on your system, this is why it tries to download Open Java.

---

