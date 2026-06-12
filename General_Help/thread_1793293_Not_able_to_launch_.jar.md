---
title: "Not able to launch .jar"
date: 2011-06-29
forum: General Help
---

### Post by gooeysan on 2011-06-29
i run xubuntu 10.04 and for the past 2 hours i was trying to launch a .jar file and finnaly when i installed java properly this happened:```
sasha@sasha-laptop:~$ java -jar '/home/sasha/Desktop/Minecraft stuff/minecraft.jar'
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.10)
   at javax.swing.plaf.basic.BasicLookAndFeel.initialize(libgcj.so.10)
   at javax.swing.UIManager.setLookAndFeel(libgcj.so.10)
   at javax.swing.UIManager.<clinit>(libgcj.so.10)
   at java.lang.Class.initializeClass(libgcj.so.10)
   at net.minecraft.LauncherFrame.main(LauncherFrame.java:154)
   at net.minecraft.MinecraftLauncher.main(MinecraftLauncher.java:13)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.10)
   at java.lang.Runtime.loadLibrary(libgcj.so.10)
   at java.lang.System.loadLibrary(libgcj.so.10)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.10)
   at java.lang.Class.initializeClass(libgcj.so.10)
   at java.lang.Class.forName(libgcj.so.10)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.10)
   ...6 more
sasha@sasha-laptop:~$ 

```

---

### Post by Azdour on 2011-06-29
Hi,

There is an old thread but it might shine some light on your issue:

[http://ubuntuforums.org/showthread.php?t=777238](http://ubuntuforums.org/showthread.php?t=777238)

What version of Java are you using and what does the following command display:

```
java -version
```

---

