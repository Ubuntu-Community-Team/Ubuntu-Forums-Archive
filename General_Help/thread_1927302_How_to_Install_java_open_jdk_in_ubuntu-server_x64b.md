---
title: "How to Install java open jdk in ubuntu-server x64bits"
date: 2012-02-17
forum: General Help
---

### Post by tester100 on 2012-02-17
Hi guys

i have installed a fresh copy of ubuntu-server 10.04 x64bits therefore i needed to install the java open jdk and open jre...

because i could not install it via apt-get install xxxx as it only works on 32bit ubuntu-server i have installed it manually.

Downloaded the jdk1.6.0_31 version from java website for the x64bits version and installed it manually in usr/local/jdk1.6.0_31   folder

then opened file etc/bash.bashrc and added the following

PATH=$PATH:/usr/local/jdk1.6.0_31/bin
export PATH
export JAVA_HOME="/usr/local/jdk1.6.0_31/bin;"
export PATH=$PATH:/usr/local/(jdk1.6.0_31)/jre/bin;
export PATH=$PATH:/usr/local/(jdk1.6.0_31)/jre;


then opened the /etc/profile file and added the following

export PATH=$PATH:/usr/local/(jdk1.6.0_31)/jre/bin
export PATH=$PATH:/usr/local/(jdk1.6.0_31)/jre


now my problem is i am trying to compile a program which calls out for javac from java jdk but i keep getting the same error about java_home cannot execute

Error: JAVA_HOME is not defined correctly.
  We cannot execute /usr/local/jdk1.6.0_31/bin/bin/java

any hints on how to setup correctly on ubuntu 64bits ?

thxs in advance

---

### Post by forestG on 2012-03-18
Hi!

you sould install synaptic first. write sudo apt-get install synaptic. 
Then open synaptic and there you can search for openjdk. Then you can install it. I have ubuntu 64-bit and it works fine.

---

