---
title: "Juniper Network Connect and 10.04 NR"
date: 2010-05-07
forum: General Help
---

### Post by chetman on 2010-05-07
Friends,

I have a brand new Acer netbook happily running UNBR, but I'd be just a little bit happier if I could get it to connect to my corporate VPN. ;)

I've done a bit of googling and reading both here and at the Juniper forums site, and it sure *looks* like folks have had some success with this. That's encouraging! What's vexing me right now, though, is that I appear to be having a problem unique to me. :(

My Java is, I think, right:

```
chet@tiny:~$ java -version
java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) Client VM (build 16.3-b01, mixed mode, sharing)

```

Also, when I do the "do I have Java?" test at the Java site, it reports my browser and Java are all up to date and happy.

However, when I log into my SA2500's portal and start Network Connect, I get this Java error:

```
java.lang.ClassFormatError: Incompatible magic value 171731060 in class file SecureNCLauncher
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClassCond(ClassLoader.java:632)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:616)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:141)
	at sun.plugin2.applet.Applet2ClassLoader.findClass(Applet2ClassLoader.java:208)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:248)
	at sun.plugin2.applet.Plugin2ClassLoader.loadCode(Plugin2ClassLoader.java:520)
	at sun.plugin2.applet.Plugin2Manager.createApplet(Plugin2Manager.java:2940)
	at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1444)
	at java.lang.Thread.run(Thread.java:619)
Exception: java.lang.ClassFormatError: Incompatible magic value 171731060 in class file SecureNCLauncher
```

I'd love to figure out what's going on here, but I'm at a loss. Does anyone have any suggestions or pointers they could share with me? Thanks in advance.

Best,
Chet

---

### Post by PugTheBlack on 2010-05-14
You running on 32 or 64 bit Ubuntu? 

Either way I have had great success on Ubuntu 10.04 following the Mad Scientist's guide, I like this way much better than the "faketun" method :-) 

[Using Juniper Network Connect on Ubuntu]("http://mad-scientist.net/juniper.html")

Hope this can help you solve your problem. 

-M-

---

