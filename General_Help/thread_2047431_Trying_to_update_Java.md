---
title: "Trying to update Java"
date: 2012-08-24
forum: General Help
---

### Post by imnotanerd on 2012-08-24
I have [followed this guide to install the JRE]("http://www.liberiangeek.net/2012/04/install-oracle-java-runtime-jre-7-in-ubuntu-12-04-precise-pangolin/"), and I used it to install JRE1.7.0_05. Now JRE1.7.0_06 is out, and I'm getting popups for updating Java. I've used the guide again, and I'm still getting popups. Any idea on how to help me fix this?

---

### Post by raja.genupula on 2012-08-24
try this :```
 javac -version
```
```
raja@badfox:~$ javac -version
javac 1.6.0_24
raja@badfox:~$ 

```

---

### Post by imnotanerd on 2012-08-24
[HTML]imnotanerd@sys76laptop:~$ javac -version
The program 'javac' can be found in the following packages:
 * default-jdk
 * ecj
 * gcj-4.6-jdk
 * openjdk-6-jdk
 * gcj-4.5-jdk
 * openjdk-7-jdk
Try: sudo apt-get install <selected package>
imnotanerd@sys76laptop:~$ java -version
java version "1.7.0_03"
OpenJDK Runtime Environment (IcedTea7 2.1.1pre) (7~u3-2.1.1~pre1-1ubuntu3)
OpenJDK 64-Bit Server VM (build 22.0-b10, mixed mode)
imnotanerd@sys76laptop:~$[/HTML]

What the? I thought I updated to 1.7.0_05.

---

### Post by QIII on 2012-08-25
Although I like much about liberiangeek, there is some stuff that is outdated and just plain bad.  That method is both.

You apparently do not have Oracle Java 7 installed properly.

Java can be installed very easily with much less headache.  Several versions of Java can coexist on a machine and you can choose between them.  The browser plugin is not so easy to change sometimes.

First, there is *no need *to get rid of OpenJDK (Update 3 is the latest, I think).  However, a very nasty "escape" vulnerability has been discovered in all versions prior to Update 5, so you should have Update 6 (the latest) installed.  Since OpenJDK lags behind Oracle Java by a couple of versions, Oracle Java 7 is probably the way to go right now.  (Oracle is heavily involved in the development of OpenJDK, with is the open source reference implementation of Oracle Java).  Normally I would say to use OpenJDK because it is open source.  However, some websites do not recognize it and there is also the problem of the "escape" exploit.

Please see the Java wiki in my signature.  In the Oracle Java 7 section, under "Command line methods", find the link "Using webupd8.org's strikingly simple method".  The most current Oracle Java 7 update will be downloaded and installed and the most recent browser plugin will replace what you currently have.  The JRE will also be set to Oracle Java 7 Update 6.

The beauty of doing this is that the next time Oracle releases a Java update it will be installed right along with all of your other updates when you do your periodic updates.

If you want to be sure you are using the Oracle Java 7 Update 6 JRE, scroll down to the section "Choosing the default Java to use."

---

### Post by imnotanerd on 2012-08-25
That was surprisingly simple! "java -version" returns 1.7.0_06 now. But Chrome still has the popup for updating Java, and icedtea-7-plugin looks like it only works for OpenJDK.

---

### Post by imnotanerd on 2012-08-25
Even a reboot gives no justice.

---

