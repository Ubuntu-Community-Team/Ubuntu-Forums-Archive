---
title: "Javac: wrong path (?)"
date: 2009-11-02
forum: General Help
---

### Post by infestor on 2009-11-02
i am a beginner in java and i need to compile a java file using javac command. but when i try to run it i get this:

```
sterz@sterz-machine:~$ javac searchcmd.java 
The program 'javac' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.4-jdk
 * gcj-4.3
 * jikes-classpath
 * jikes-kaffe
 * kaffe
 * sun-java6-jdk
Try: sudo apt-get install <selected package>
javac: command not found

```if it helps:
```

sterz@sterz-machine:~$ sudo update-alternatives --config java
There is only one alternative in link group java: /usr/lib/jvm/java-6-sun/jre/bin/java
Nothing to configure.
```

also jdk1.6.0_16 is installed on my home directory

---

### Post by liquidbee on 2009-11-02
Why are you trying to configure java while referring to javac ?

```
sudo apt-get install sun-java6-jdk sun-java6-fonts
sudo update-alternatives --config javac
```

---

### Post by infestor on 2009-11-02
thanks that worked...was it that i did not run "sudo update-alternatives --config javac"?
i'm just curious. 'cos i am sure i had sun-jdk thats what netbeans needed to run.

---

### Post by liquidbee on 2009-11-02
> **infestor said:**
> thanks that worked...was it that i did not run "sudo update-alternatives --config javac"?
i'm just curious. 'cos i am sure i had sun-jdk thats what netbeans needed to run.

JDK is a development kit ( compiler ) - NetBeans doesn't require it to be installed on your machine ( unless you want to develop Java applications ).

---

