---
title: "Minecraft in Ubuntu"
date: 2011-03-28
forum: General Help
---

### Post by Tchoob on 2011-03-28
I tried to install the openJDK using:

```
sudo apt-get install openjdk-6-jre openjdk-6-jre-headless

```

and got the following:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openjdk-6-jre is already the newest version.
openjdk-6-jre-headless is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

So I have Minecraft installed in my home folder, I renamed it to *Minecraft.jar* and then tried to run it using:

```
java -Xmx1024M -Xms512M -cp Minecraft.jar net.minecraft.LauncherFrame
```

But I got the following message:

```
Exception in thread "main" java.lang.NoClassDefFoundError: net/minecraft/LauncherFrame
Caused by: java.lang.ClassNotFoundException: net.minecraft.LauncherFrame
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: net.minecraft.LauncherFrame. Program will exit.
```

I'm no expert at terminal, and I have no idea what that means. Can anyone help? I've been trying to get Minecraft to run for the longest time and I can't seem to be able to do it. Thanks in advance.

---

### Post by Tchoob on 2011-03-28
Actually, I installed the package for Sun Java 6 Runtime. I go to the file, right-click, select "Open With Sun Java 6 Runtime"... and nothing happens. Nothing at all. New problem.

Anyone know what to do?

---

### Post by seawolf167 on 2011-03-29
I haven't set it up myself, but see if [this ]("http://timashley.me/node/596")helps you.

---

### Post by Tchoob on 2011-03-30
After going through those instructions, I get this error:

```
Exception in thread "main" java.lang.ClassNotFoundException: net.minecraft.LauncherFrame
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
	at Loader.load(Loader.java:25)
	at Loader.main(Loader.java:19)
```

---

