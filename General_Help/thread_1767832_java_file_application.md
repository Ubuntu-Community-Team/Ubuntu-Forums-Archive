---
title: "java file application"
date: 2011-05-26
forum: General Help
---

### Post by ccsi on 2011-05-26
hi every one here 

I have TinyOs application that work with Telosb platform, and this application already has GUI .Java file are existed , I want to compile these file so that i can see the interface.

1- should I put these folder under TinyOS/ app ?

2- I type : javac *.java to compile all those java files but there are 28 errors     :

MainFrame.java:23: package tinyOS[COLOR=Red] does not exist[/COLOR]
[COLOR=Red]import tinyOS.connecter_tracking;[/COLOR]
             ^
MainFrame.java:28: cannot find symbol
symbol  : class liveMonitoring_frame
location: class GUI.MainFrame
   liveMonitoring_frame w1;
....
....

so  what do think ..
thanks in advanced

---

### Post by ccsi on 2011-05-26
NOW  i compile all existed  java files with 
javac   *.java

and try to run the main file MainFrame with 

java  
MainFrame

but the result is :

user@ubuntu:~/Desktop/TAPMcode/Java-Code/GUI$ java MainFrame
Exception in thread "main" java.lang.NoClassDefFoundError: MainFrame (wrong name: GUI/MainFrame)
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
Could not find the main class: MainFrame. Program will exit.
   ??

any help since I checked java version and it is uptodate

---

