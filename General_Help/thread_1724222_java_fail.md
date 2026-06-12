---
title: "java fail"
date: 2011-04-08
forum: General Help
---

### Post by kailkitsune on 2011-04-08
java ran just fine with 10.04 but when i upgrade to 10.10 it stopped working i can not get any of my java files to load, when i dub-click them my cpu spikes then nodda.
am i the only one with this problem?

---

### Post by veggen on 2011-04-08
Try running from terminal, just to see if you get some error message.
Anyway, since it's pretty harmless, I'd just nuke java and then reinstall.
Which one are you using, Sun or OpenJDK? If you have both installed, try selecting the alternative one.

---

### Post by kailkitsune on 2011-04-08
I'm using OpenJDK, and the reinstall didn't help T_T

this is my minecraft terminal out put(it loads into a black screen).

 bourbon@This-is-my-name:~$ padsp java -jar $HOME/Documents/minecraft/minecraft.jar
java.io.IOException: Cannot run program "javaw": java.io.IOException: error=2, No such file or directory
    at java.lang.ProcessBuilder.start(ProcessBuilder.java:475)
    at net.minecraft.MinecraftLauncher.main(MinecraftLauncher.java:31)
Caused by: java.io.IOException: java.io.IOException: error=2, No such file or directory
    at java.lang.UNIXProcess.<init>(UNIXProcess.java:164)
    at java.lang.ProcessImpl.start(ProcessImpl.java:81)
    at java.lang.ProcessBuilder.start(ProcessBuilder.java:468)
    ... 1 more
144 recipes
Setting user: kailkitsune, -6981731511402216251
Exception in thread "Minecraft main thread" java.lang.LinkageError: Version mismatch: jar version is '17', native libary version is '18'
    at org.lwjgl.Sys.<clinit>(Sys.java:103)
    at org.lwjgl.opengl.Display.<clinit>(Display.java:129)
    at net.minecraft.client.Minecraft.a(SourceFile:219)
    at net.minecraft.client.Minecraft.run(SourceFile:638)
    at java.lang.Thread.run(Thread.java:636)


and this is my Frozen terminal output (won't load at all).

bourbon@This-is-my-name:~$ padsp java -jar $HOME/Documents/Frozen.jar
Exception in thread "main" java.lang.NoClassDefFoundError: com/jme3/input/controls/ActionListener
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
Caused by: java.lang.ClassNotFoundException: com.jme3.input.controls.ActionListener
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
    ... 11 more
Could not find the main class: mygame.Main. Program will exit.

---

