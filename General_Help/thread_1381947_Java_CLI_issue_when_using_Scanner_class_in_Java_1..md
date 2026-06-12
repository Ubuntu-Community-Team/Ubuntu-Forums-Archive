---
title: "Java CLI issue when using Scanner class in Java 1.6 and later"
date: 2010-01-15
forum: General Help
---

### Post by teward on 2010-01-15
Okay, using the Scanner class within Java, I cannot run the programs in the terminal.  It returns this error:
```
Exception in thread "main" java.lang.NoClassDefFoundError: java.util.Scanner
   at LabOne.main(LabOne.java:44)
```

The only version of Java installed is recent, so why is it returning this and how do I fix it?

---

### Post by doas777 on 2010-01-15
usually a classdef error on scanner indicates that your jre or your jdk is 1.4 or lower. 

what is the output of 
```
javac --version
```

have you installed the sun java jdk?
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

be sure to update the alternatives per the link. many people install the correct java but forget to tell their systems to use it by default.

---

### Post by teward on 2010-01-15
Well, the ONLY Java in my system was 1.6.  Initially, it wouldn't run the auto-installer so I had to manually install, but its the same as the most recent version anyways.

I'm 100% certain its 1.6, but I'll check the link and get back to you.

---

### Post by doas777 on 2010-01-15
did you run this after install?
```
sudo update-java-alternatives -s java-6-sun
```

---

### Post by teward on 2010-01-15
```
me@me:~$ javac -version
Eclipse Java Compiler 0.894_R34x, 3.4.2 release, Copyright IBM Corp 2000, 2008. All rights reserved.

me@me:~$ sudo update-java-alternatives -l
[sudo] password:
java-6-sun 63 /usr/lib/jvm/java-6-sun
java-gcj 1042 /usr/lib/jvm/java-gcj
```

I do have sun Java installed, so perhaps I should uninstall Eclipse...

---

### Post by doas777 on 2010-01-15
yeah, that is not a normal compiler version

```
karmic:~$ javac -version
javac 1.6.0_0

```

I always install java first, then eclipse (and from the repos) but no idea if that would make a diff.

---

### Post by teward on 2010-01-15
Alright, let me test this now...

okay, first thing:  javac now uses 1.6.0.

second: the command java does not work, it reports its version:
```
me@me:~/Desktop/15-121/Programs/Lab1$ java -version
java version "1.5.0"
gij (GNU libgcj) version 4.3.3

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```How can I set it up to work with 1.6 instead of 1.5?

***EDIT: I'm going into Synaptic and reinstalling the sun java program files (all of them, JRE, JDK, etc).  I'll see if that works.  NOTE: It didnt work.***

---

### Post by doas777 on 2010-01-15
> **TrekCaptainUSA said:**
> Alright, let me test this now...

okay, first thing:  javac now uses 1.6.0.

second: the command java does not work, it reports its version:
```
me@me:~/Desktop/15-121/Programs/Lab1$ java -version
java version "1.5.0"
gij (GNU libgcj) version 4.3.3

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```How can I set it up to work with 1.6 instead of 1.5?

ahh thats it. not the compiler but the runtime (although util.scanner shoudl be in 1.5).

have you installed all the packages on this list?
[http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/](http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/)

---

### Post by teward on 2010-01-15
Did this ```
$ sudo update-java-alternatives -s java-6-sun
```

It reset the version.  That works for me.  :)

---

