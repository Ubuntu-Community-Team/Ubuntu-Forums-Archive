---
title: "How do I set up JDK?"
date: 2011-10-17
forum: General Help
---

### Post by xVehemencityx on 2011-10-17
Hi.  I just switched to Ubuntu because I feel that it's more productive for programming, but I can't seem to get JDK working.  I installed open-jdk-1.7.0, and open-jre was installed when I installed Ubuntu.  I made a simple Hello World program, and it had no trouble compiling the class, but when I tried to run it via "java HelloWorld", it throws a fit.


```
Exception in thread "main" java.lang.UnsupportedClassVersionError: HelloWorld : Unsupported major.minor version 51.0
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:634)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:277)
	at java.net.URLClassLoader.access$000(URLClassLoader.java:73)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:212)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: HelloWorld. Program will exit.

```

---

### Post by 11jmb on 2011-10-17
just to make sure nothing is wrong there, please post your code

---

### Post by xVehemencityx on 2011-10-17
```
public class HelloWorld {

    // method main(): ALWAYS the APPLICATION entry point
    public static void main (String[] args) {
	System.out.println ("Hello World!");
    }
}
```

---

### Post by 11jmb on 2011-10-17
Thanks. I just wanted to make sure you didnt do anything crazy with your code.

That error comes up when your compiler and JVM are incompatible versions. How did you go about installing them?

---

### Post by xVehemencityx on 2011-10-17
I just used the Software Center and installed open-jdk 1.7, and open-jre was already installed.

---

### Post by Prescilla on 2011-10-18
I have the same problem. Please help!

---

### Post by maxino on 2011-10-21
Hi,
I think you may have a mismatch between the versions of java and javac.
On my system the two versions are the same and I have no problem compiling and running classes:

```
$ java -version
java version "1.6.0_23"
OpenJDK Runtime Environment (IcedTea6 1.11pre) (6b23~pre10-0ubuntu5)
OpenJDK Client VM (build 20.0-b11, mixed mode, sharing)
$ javac -version
javac 1.6.0_23
```

Try removing openjdk-7-jdk and install openjdk-6-jdk:

```
sudo apt-get remove openjdk-7-jdk
sudo apt-get install openjdk-6-jdk

```

Hope it helps,

---

### Post by Attempt#2 on 2012-01-04
Anybody manage to fix this?

---

### Post by maxino on 2012-01-06
[http://ubuntuforums.org/showthread.php?t=1903414](http://ubuntuforums.org/showthread.php?t=1903414)

---

