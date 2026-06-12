---
title: "freecol doesnt run"
date: 2010-01-13
forum: General Help
---

### Post by mikulopm on 2010-01-13
hi

i installed game freecol on my ubuntu 9.10 from ubuntu software center. but if i want to run it from menu it doesnt run. if i run it from terminal i get this report:

```
root@mikulopm-laptop:~# /usr/games/freecol
Exception in thread "main" java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-openjdk/jre/lib/i386/xawt/libmawt.so
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1646)
    at java.lang.Runtime.load0(Runtime.java:787)
    at java.lang.System.load(System.java:1022)
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1747)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1664)
    at java.lang.Runtime.loadLibrary0(Runtime.java:840)
    at java.lang.System.loadLibrary(System.java:1047)
    at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
    at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.awt.Toolkit.loadLibraries(Toolkit.java:1614)
    at java.awt.Toolkit.<clinit>(Toolkit.java:1636)
    at java.awt.Dimension.<clinit>(Dimension.java:87)
    at net.sf.freecol.FreeCol.<clinit>(FreeCol.java:106)
Could not find the main class: net.sf.freecol.FreeCol. Program will exit.
```btw i uninstalled then freecol using ubuntu software centrer and tryed to install it from .jar and from tar.gz with the same result...

i am new in ubuntu... some things i can google, but this is too much for me...
could someone help me, what is going on?
i have sun java 6 runtime installed
thanks :)

---

### Post by akakingess on 2010-01-13
I installed it and it ran fine, running 9.10 64-bit, now we have to look at whether or not Java is installed correctly or in the correct locations that would apply to this application. Have you installed the JRE (Java Runtime Environment), and if not we can start from there, but don't lose hope as we will get you there one way or another.

---

### Post by mikulopm on 2010-01-13
> **akakingess said:**
> I installed it and it ran fine, running 9.10 64-bit, now we have to look at whether or not Java is installed correctly or in the correct locations that would apply to this application. Have you installed the JRE (Java Runtime Environment), and if not we can start from there, but don't lose hope as we will get you there one way or another.

i installed java 6 runtime from ubuntu software center, so the location of java should be default.

```
root@mikulopm-laptop:~# java -version
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.6.1) (6b16-1.6.1-3ubuntu1)
OpenJDK Server VM (build 14.0-b16, mixed mode)

```thanks fo quick response btw ;)
 
edit: i forgot, i am running dualboot ubuntu 9.10 32-bit with vista (vista was first on my laptop)

---

### Post by akakingess on 2010-01-13
> **mikulopm said:**
> i installed java 6 runtime from ubuntu software center, so the location of java should be default.

```
root@mikulopm-laptop:~# java -version
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.6.1) (6b16-1.6.1-3ubuntu1)
OpenJDK Server VM (build 14.0-b16, mixed mode)

```thanks fo quick response btw ;)
 
edit: i forgot, i am running dualboot ubuntu 9.10 32-bit with vista (vista was first on my laptop)

I see that you have IcedTea installed, that may be causing some conflicts, so i would suggest uninstalling that, with the knowledge that we could always try to reinstall at a later time if it doesn't turn out to have anything to do with our problem.

---

### Post by mikulopm on 2010-01-13
> **akakingess said:**
> I see that you have IcedTea installed, that may be causing some conflicts, so i would suggest uninstalling that, with the knowledge that we could always try to reinstall at a later time if it doesn't turn out to have anything to do with our problem.

  how shoud i do that?

actually, i uninstalled openJDK java runtime in ubuntu software center and installed sun java runtime so i dont understand why its using openJDK java runtime...

---

### Post by akakingess on 2010-01-13
> **mikulopm said:**
> how shoud i do that?

actually, i uninstalled openJDK java runtime in ubuntu software center and installed sun java runtime so i dont understand why its using openJDK java runtime...

That is another good question, about the JDK vs. JRE, really you should need the JRE to play a game within the Java Runtime Environment, but first to the IcedTea issue, IcedTea is Ubuntu's version of JRE without going into more detail, so I would uninstall Iced Tea and then do an uninstall and reinstall of the Java utilities that you need and/or want. In other words, uninstall IcedTea via the Synaptic Package Manager and then install both JRE and JDK (for future use, just in case) via the sun.com/java web site and be sure to download the version you need, 32 or 64 bit. If you are not sure which Ubuntu you are running the enter uname -a in a terminal and the output should tell you, sometimes 64-bit will show as x86_64, but you get the idea, just be sure to get and install the proper version of Java, and I reccommend the version from the Sun web site (especially if going with the 64-bit version. I have to run but will be back in a couple of hours and will check in to see what progress you have made.

---

### Post by mikulopm on 2010-01-13
> **akakingess said:**
> That is another good question, about the JDK vs. JRE, really you should need the JRE to play a game within the Java Runtime Environment, but first to the IcedTea issue, IcedTea is Ubuntu's version of JRE without going into more detail, so I would uninstall Iced Tea and then do an uninstall and reinstall of the Java utilities that you need and/or want. In other words, uninstall IcedTea via the Synaptic Package Manager and then install both JRE and JDK (for future use, just in case) via the sun.com/java web site and be sure to download the version you need, 32 or 64 bit. If you are not sure which Ubuntu you are running the enter uname -a in a terminal and the output should tell you, sometimes 64-bit will show as x86_64, but you get the idea, just be sure to get and install the proper version of Java, and I reccommend the version from the Sun web site (especially if going with the 64-bit version. I have to run but will be back in a couple of hours and will check in to see what progress you have made.


well, i uninstalled everything thats connected with java and installed again sun java and its working :)

so thank you very much for help

---

### Post by akakingess on 2010-01-13
> **mikulopm said:**
> well, i uninstalled everything thats connected with java and installed again sun java and its working :)

so thank you very much for help

No problem whatsoever, now if you don't mind, please mark your Thread as SOLVED using the Thread Tools at the top of the thread. That way, others with the same issue will see yours and the fact that it was solved and will not have to start another thread on the subject.  Thank you and happy learning.

---

