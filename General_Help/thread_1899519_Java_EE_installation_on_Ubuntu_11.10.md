---
title: "Java EE installation on Ubuntu 11.10"
date: 2011-12-23
forum: General Help
---

### Post by ChrisSocha on 2011-12-23
Good day all,

I have a (hopefully simple) question regarding the installing of Java EE on Ubuntu 11.10

I downloaded Java EE SDK 6 ([java_ee_sdk_6u3-unix.sh]("http://www.oracle.com/technetwork/java/javaee/downloads/java-ee-sdk-6u3-downloads-439814.html")) from the Oracle website, and ran it with the correct execute privileges. It appeared to install fine, but when i check the version i get the following:
```
chris@Socha-Netbook:~$ java -version
java version "1.6.0_23"
OpenJDK Runtime Environment (IcedTea6 1.11pre) (6b23~pre11-0ubuntu1.11.10)
OpenJDK Server VM (build 20.0-b11, mixed mode)
```... and when seeing if i can set it as an alternative i get:

```
~$ sudo update-alternatives --config java
There is only one alternative in link group java: /usr/lib/jvm/java-6-openjdk/jre/bin/java
Nothing to configure.
```Am i missing a key step? Have i actually installed the right files? I am installing this with the intent of developing Java using Eclipse.

Thanks in advance for any help!
(And Merry XMas all!)

---

### Post by QIII on 2011-12-23
The SDK is not going to show up on your alternatives.  The JRE does.  

SDK is the toolkit you use to develop in Java EE, of course.  The JRE is the runtime environment and most people also use it for the Java plugin for their browser.

Please follow the instructions here to install the JRE.

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

I'd install the entire JDK, by the way.

When you install Eclipse, you will have to specify the SDK/JDK to use.  It should go hunting for it and add it as a suggestion.

---

