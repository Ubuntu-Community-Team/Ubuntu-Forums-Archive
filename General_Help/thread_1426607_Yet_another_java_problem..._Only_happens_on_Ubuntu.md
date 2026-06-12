---
title: "Yet another java problem... Only happens on Ubuntu for some reason..."
date: 2010-03-10
forum: General Help
---

### Post by nickguletskii on 2010-03-10
Yep, I need Java on Ubuntu.

I have installed Java, thanks to the guy who gave me a link to a guide, but now a very weird error occurs when I try to exec a jar using javaws:

```
MissingFieldException[ The following required field is missing from the launch file: <jnlp>]
	at com.sun.javaws.jnl.XMLFormat.parse(Unknown Source)
	at com.sun.javaws.jnl.LaunchDescFactory.buildDescriptor(Unknown Source)
	at com.sun.javaws.jnl.LaunchDescFactory.buildDescriptor(Unknown Source)
	at com.sun.javaws.jnl.LaunchDescFactory.buildDescriptor(Unknown Source)
	at com.sun.javaws.Main.launchApp(Unknown Source)
	at com.sun.javaws.Main.continueInSecureThread(Unknown Source)
	at com.sun.javaws.Main$1.run(Unknown Source)
	at java.lang.Thread.run(Unknown Source)

```

In terminal, using command java, I get a standard MainClassDef not found error, although the jar works perfectly under Windows.

Any ideas?

---

### Post by no2498 on 2010-03-10
ubuntu is not windows
windows uses exe type files ubuntu does not

---

### Post by Sub101 on 2010-03-10
> **no2498 said:**
> ubuntu is not windows
windows uses exe type files ubuntu does not

Running a jar shouldnt really matter, Java is after all meant to be write once run anywhere. 

As to your problem, does running just ```
javaws
``` work?

---

### Post by nickguletskii on 2010-03-11
No, it wants openjdk while I have Sun jre installed.

---

### Post by nickguletskii on 2010-03-12
Anybody? I have followed this tutorial: [http://sites.google.com/site/easylinuxtipsproject/java]("http://sites.google.com/site/easylinuxtipsproject/java")

---

### Post by Sub101 on 2010-03-12
> **nickguletskii said:**
> No, it wants openjdk while I have Sun jre installed.

Sorry, by it wants openJDK what do you mean?

Does running javaws alone work or produce errors?

---

### Post by nickguletskii on 2010-03-12
It says javaws is not installed, but when I do this: ```
java
``` it gives me a list of args.

---

### Post by Sub101 on 2010-03-12
What is your output of:

```
java -version
```

---

### Post by nickguletskii on 2010-03-12
1.6.0_18

---

### Post by nickguletskii on 2010-03-12
More info: terminal:

```
root@clientbox:/media/INTENSO# java lejosclu.jar
Exception in thread "main" java.lang.NoClassDefFoundError: lejosclu/jar
Caused by: java.lang.ClassNotFoundException: lejosclu.jar
	at java.net.URLClassLoader$1.run(Unknown Source)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(Unknown Source)
	at java.lang.ClassLoader.loadClass(Unknown Source)
	at sun.misc.Launcher$AppClassLoader.loadClass(Unknown Source)
	at java.lang.ClassLoader.loadClass(Unknown Source)
Could not find the main class: lejosclu.jar.  Program will exit.

```

---

### Post by anishkthomas on 2010-03-12
If your's architecture is AMD 64 bit, then java webstart wont be supported in JDK 1.6 release. It will be only supported in dolphin (JDK 1.7) release.

See the bug [http://bugs.sun.com/view_bug.do?bug_id=4802695](http://bugs.sun.com/view_bug.do?bug_id=4802695)

---

### Post by Sub101 on 2010-03-12
> **nickguletskii said:**
> More info: terminal:

```
root@clientbox:/media/INTENSO# java lejosclu.jar.

```

To run a jar you must use:

```
java -jar lejosclu.jar
```

and I wasnt aware of that bug.... sorry.

---

### Post by nickguletskii on 2010-03-13
Bump?

---

### Post by Chronon on 2010-03-13
What architecture are you using?  You never said.  If it's x86_64 then it is to be expected that there's no javaws (as anishkthomas pointed out).

---

### Post by nickguletskii on 2010-03-13
I have 32 bit... i386.

---

