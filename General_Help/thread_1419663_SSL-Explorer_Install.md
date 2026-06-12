---
title: "SSL-Explorer Install"
date: 2010-03-02
forum: General Help
---

### Post by glennbtn on 2010-03-02
Hi All

I am trying to install ssl explorer on my 8.04 server. I have followed an old document and installed java 5 and tried the install and got the following

root@ssl:/usr/src/sslexplorer-1.0.0_RC17# ant install
Buildfile: build.xml

install:

compile-dependencies:

compile:
    [javac] Compiling 15 source files to /usr/src/sslexplorer-1.0.0_RC17/maverick-util/build/classes
    [javac] source level should be comprised in between '1.3' and '1.6' (or '5', '5.0', ..., '7' or '7.0'): 1.1

BUILD FAILED
/usr/src/sslexplorer-1.0.0_RC17/build.xml:49: The following error occurred while executing this line:
/usr/src/sslexplorer-1.0.0_RC17/sslexplorer/build.xml:742: The following error occurred while executing this line:
/usr/src/sslexplorer-1.0.0_RC17/maverick-util/build.xml:44: Compile failed; see the compiler error output for details.

Can anyone tell me where I am going wrong still being a bit of a novice

---

### Post by AlexBAF on 2010-05-18
You need add paths to Java and ant

```

root@localhost:~# export JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun/
root@localhost:~# PATH=${PATH}:${JAVA_HOME}/bin
root@localhost:~# export ANT_HOME=/usr/share/ant/
root@localhost:~# PATH=${PATH}:${ANT_HOME}/bin

```

[http://doc.ubuntu-fr.org/ssl-explorer](http://doc.ubuntu-fr.org/ssl-explorer)

---

