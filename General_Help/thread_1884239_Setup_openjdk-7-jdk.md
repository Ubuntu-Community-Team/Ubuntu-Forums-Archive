---
title: "Setup openjdk-7-jdk"
date: 2011-11-20
forum: General Help
---

### Post by xtiano77 on 2011-11-20
Ubuntu 11.10

I did a fresh install of 11.10. Afterwards, I wrote and compiled a simple java class; however, when I tried to execute the .class file, it throws an exception letting me know that it cannot find the "main" method. I even tried using the "Hello World" example from the Oracle page and still didn't compile. Can anyone help me fix this? Thanks in advance.

Code from the Oracle page:

public class Test {

	public static void main(String[] args){
		System.out.println("Hello World");
	}

}

Error message:

Exception in thread "main" java.lang.UnsupportedClassVersionError: Test : Unsupported major.minor version 51.0
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
Could not find the main class: Test. Program will exit.

---

