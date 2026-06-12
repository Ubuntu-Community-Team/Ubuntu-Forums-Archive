---
title: "Cannot execute java class file in Ubuntu 9.10"
date: 2010-03-20
forum: General Help
---

### Post by tejpatil on 2010-03-20
Hi All,

I am a newbie to Ubuntu. Please help me resolving this issue with java. I installed jdk1.6.0_18 version. Please see below for the version.
++++++++++++++++++++++++++++++++++++++++
tp@tp-ubuntu:~$ java -version
java version "1.6.0_18"
Java(TM) SE Runtime Environment (build 1.6.0_18-b07)
Java HotSpot(TM) 64-Bit Server VM (build 16.0-b13, mixed mode)
++++++++++++++++++++++++++++++++++++++++

Also my echo $PATH looks like this which I have made an entry in 
/etc/environment
++++++++++++++++++++++++++++++++++++++++
tp@tp-ubuntu:~$ echo $PATH
.:/opt/java/64/jdk1.6.0_18/bin/bin:/opt/java/64/jdk1.6.0_18/bin/jre/bin:/opt/java/64/jdk1.6.0_18/bin:/opt/java/64/jdk1.6.0_18/jre/bin:.:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
++++++++++++++++++++++++++++++++++++++++++

Also my echo $CLASSPATH looks like this which I have made an entry in 
/etc/environment
+++++++++++++++++++++++++++++++++++++++++
tp@tp-ubuntu:~$ echo $CLASSPATH
JAVA_HOME="/opt/java/64/jdk1.6.0_18/lib:/opt/java/64/jdk1.6.0_18/jre/lib"
++++++++++++++++++++++++++++++++++++++++++
hello.java
I am trying to execute this program
public class hello{
   public static void main(String args[]){

System.out.println("hello");
   }
}

I compiled it successfully and created the hello.class file.
tp@tp-ubuntu:~/work$ ls
hello.class  hello.java  

But when I try to execute this i am getting following error
tp@tp-ubuntu:~/work$ java hello
Exception in thread "main" java.lang.NoClassDefFoundError: hello
Caused by: java.lang.ClassNotFoundException: hello
    at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:248)
Could not find the main class: hello.  Program will exit.

I don't know how to resolve this. Please help.

Thanks,
Tej

---

### Post by Brandon Williams on 2010-03-23
You should not need to set CLASSPATH at all if the only elements you put into it are the standard locations. unset CLASSPATH and try again.

---

