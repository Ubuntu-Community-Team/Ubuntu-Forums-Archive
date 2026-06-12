---
title: "Problem running Java application"
date: 2006-04-20
forum: General Help
---

### Post by brim4brim on 2006-04-20
Hi,

I'm trying to run a Java application and I get an error when running it.  I've got java installed with paths etc.. all setup properly (I can run eclipse and other Java apps).

However this one is causing the problem called J.  It's an IDE for a programming language.

I get an Exception in thread "main" java.lang.NoClassDefFounderror: jx/frames/J at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)

Caused by: java.lang.Class.forName (java.lang.String, boolean, java.lang.
String, boolean, java.lang.ClassLoader) (usr/lib/libgcj.so.6.0.0)
at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)

Yeah that's horrible to look at but anyway, can anyone help sort out the problem.  I'm not great at reading Java errors, it's been a while.  Note this isn't my application and I don't have access to the source code AFAIK.

---

### Post by Ensnared on 2006-04-20
My guess is you need Sun's version of Java to make it work. I've never gotten much to run with any other versions atleast.

To install it, do the following:
```
sudo apt-get install sun-j2re1.5
```
Then, to make it default for Java-applications, you do this:
```
sudo update-alternatives --config java
```
...and enter the number for Sun's JRE. Then try to run your application as normal.

---

### Post by brim4brim on 2006-04-20
[QUOTE=Ensnared]My guess is you need Sun's version of Java to make it work. I've never gotten much to run with any other versions atleast.

To install it, do the following:
```
sudo apt-get install sun-j2re1.5
```
Then, to make it default for Java-applications, you do this:
```
sudo update-alternatives --config java
```
...and enter the number for Sun's JRE. Then try to run your application as normal.[/QUOTE]

Cheers, especially for such a quick reply.  I installed this in a previous Ubuntu, didn't realise I didn't have it on my current setup.  Thanks again.

---

