---
title: "Downgrade Ant"
date: 2009-12-07
forum: General Help
---

### Post by StevenMayhew on 2009-12-07
Hi all,

I've been working on a BPM for a project that I've been working on for a while, currently I'm using jBoss AS + jBPM 4.2. I have come into a few issues, mostly with usability (its for fairly computer illiterate people and I want it to be easy to use) so I've been looking into possibly using the Seam framework instead, as it provides me with a bit more optionality in the design etc. One problem is that I can't even build it - it's complaining about a version issue with ant. I have the latest (1.7.1) installed and it requires 1.7.0

```
testbase@linux-01:~/surv/jboss-seam-2.2.0.GA$ ant build
Buildfile: build.xml

BUILD FAILED
/home/testbase/surv/jboss-seam-2.2.0.GA/build.xml:9: You are using Apache Ant version 1.7.1 compiled on October 19 2009. You must use Ant 1.7.0 to build Seam. Ant 1.7.1 has known bugs.

Total time: 0 seconds

```
 
I thought that I would just downgrade it using the package manager but it appears that there aren't any previous versions available through this method.

```
testbase@linux-01:~/surv/jboss-seam-2.2.0.GA$ sudo apt-cache showpkg ant
Package: ant
Versions: 
1.7.1-4 (/var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_karmic_main_binary-amd64_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_karmic_main_binary-amd64_Packages
                  MD5: 5ceb3b9317ae6734ab188db300acaade


Reverse Depends: 
  libmaven-invoker-plugin-java,ant
  libmaven-antrun-plugin-java,ant
  jde,ant
  velocity,ant
  testng,ant
  nice,ant
  libzeroc-ice-java,ant
  libplexus-ant-factory-java,ant
  libnb-java2-java,ant 1.7.0
  libjtidy-java,ant
  libjetty6-extra-java,ant
  libjetty-extra-java,ant
  clirr,ant
  maven-ant-helper,ant
  libow-util-ant-tasks-java,ant 1.7
  libecj-java,ant
  libaxis-java,ant
  ecj,ant
  ant-optional,ant 1.7.1-4
  ant-gcj,ant
  ant-doc,ant
Dependencies: 
1.7.1-4 - default-jre-headless (16 (null)) java1-runtime-headless (16 (null)) java2-runtime-headless (0 (null)) libxerces2-java (0 (null)) default-jdk (16 (null)) java-compiler (16 (null)) java-sdk (0 (null)) ant-doc (0 (null)) ant-optional (0 (null)) ant-gcj (0 (null)) ant-doc (1 1.6.5-1) libant1.6-java (0 (null)) ant-doc (1 1.6.5-1) libant1.6-java (0 (null)) 
Provides: 
1.7.1-4 - 
Reverse Provides: 

```

Is there a simple way for me to downgrade that I'm missing? I'm probably searching for the wrong sort of things, I haven't ever had to do anything where there wasn't an older version in aptitude - help would be appreciated.

Thanks,
Steven

---

