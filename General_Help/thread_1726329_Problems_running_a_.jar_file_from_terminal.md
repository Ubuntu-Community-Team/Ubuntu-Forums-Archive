---
title: "Problems running a .jar file from terminal"
date: 2011-04-11
forum: General Help
---

### Post by Rikeshar on 2011-04-11
Hello everyone, I'm trying to run a .jar file from the terminal (so that I can set up a launcher) but I can't seem to get it to work. The file is marked as an executable, and all works fine if right click the file and open with java in gui, but when I enter:

```
java -jar minecraft.jar
```

... from the directory the jar is located in, I get:

```

zach@zach-ubuntu:~$ java -jar minecraft.jar
java.io.IOException: Cannot run program "javaw": java.io.IOException: error=2, No such file or directory
    at java.lang.ProcessBuilder.start(ProcessBuilder.java:475)
    at net.minecraft.MinecraftLauncher.main(MinecraftLauncher.java:31)
Caused by: java.io.IOException: java.io.IOException: error=2, No such file or directory
    at java.lang.UNIXProcess.<init>(UNIXProcess.java:164)
    at java.lang.ProcessImpl.start(ProcessImpl.java:81)
    at java.lang.ProcessBuilder.start(ProcessBuilder.java:468)
    ... 1 more
Exception in thread "main" java.awt.HeadlessException
    at java.awt.GraphicsEnvironment.checkHeadless(GraphicsEnvironment.java:173)
    at java.awt.Window.<init>(Window.java:437)
    at java.awt.Frame.<init>(Frame.java:419)
    at net.minecraft.LauncherFrame.<init>(LauncherFrame.java:27)
    at net.minecraft.LauncherFrame.main(LauncherFrame.java:158)
    at net.minecraft.MinecraftLauncher.main(MinecraftLauncher.java:36)
zach@zach-ubuntu:~$ java -jar minecraft.jar
java.io.IOException: Cannot run program "javaw": java.io.IOException: error=2, No such file or directory
    at java.lang.ProcessBuilder.start(ProcessBuilder.java:475)
    at net.minecraft.MinecraftLauncher.main(MinecraftLauncher.java:31)
Caused by: java.io.IOException: java.io.IOException: error=2, No such file or directory
    at java.lang.UNIXProcess.<init>(UNIXProcess.java:164)
    at java.lang.ProcessImpl.start(ProcessImpl.java:81)
    at java.lang.ProcessBuilder.start(ProcessBuilder.java:468)
    ... 1 more
Exception in thread "main" java.awt.HeadlessException
    at java.awt.GraphicsEnvironment.checkHeadless(GraphicsEnvironment.java:173)
    at java.awt.Window.<init>(Window.java:437)
    at java.awt.Frame.<init>(Frame.java:419)
    at net.minecraft.LauncherFrame.<init>(LauncherFrame.java:27)
    at net.minecraft.LauncherFrame.main(LauncherFrame.java:158)
    at net.minecraft.MinecraftLauncher.main(MinecraftLauncher.java:36)

```

I'm not sure how to read this error... can someone help?

---

### Post by satish_j on 2011-04-11
this is really strange:-k.If it is working from right-click-open,then it should also work with java -jar
may be you should try re-installing jre...

---

### Post by mcduck on 2011-04-11
Try this, it's what I'm using to launch Minecraft:

java -cp /*path*/*to*/minecraft.jar net.minecraft.LauncherFrame

---

### Post by mendhak on 2011-04-11
Just to add to the mix, I run it like this

java -Xmx1024M -Xms512M -cp Minecraft.jar net.minecraft.LauncherFrame

---

### Post by Rikeshar on 2011-04-11
Hm.. tried both of those (the last one I had sort of tried, incidentally, except I was using 1024M as both the minimum and max, like when running the server) but with no change. Still getting

```

zach@zach-ubuntu:~/Desktop$ java -Xmx1024M -Xms512M -cp /home/zach/Desktop/Minecraft.jar net.minecraft.LauncherFrame
Exception in thread "main" java.awt.HeadlessException
    at java.awt.GraphicsEnvironment.checkHeadless(GraphicsEnvironment.java:173)
    at java.awt.Window.<init>(Window.java:437)
    at java.awt.Frame.<init>(Frame.java:419)
    at net.minecraft.LauncherFrame.<init>(LauncherFrame.java:27)
    at net.minecraft.LauncherFrame.main(LauncherFrame.java:158)
zach@zach-ubuntu:~/Desktop$ 

```It's the strangest thing, because it was working fine for me before, I format the drive and reinstalled Ubuntu 10.10 (11.04 was just a little bit too buggy for me still) and now it's a no go. I've got Sun Java 6 installed.

**EDIT**

While I had Sun Java installed, it wasn't the default java. Made it default and all is well.

---

### Post by luigi_mb on 2011-04-11
> **Rikeshar said:**
> Hello everyone, I'm trying to run a .jar file from the terminal (so that I can set up a launcher) but I can't seem to get it to work. The file is marked as an executable, and all works fine if right click the file and open with java in gui, but when I enter:

```
java -jar minecraft.jar
```

... from the directory the jar is located in, I get:

[code]
zach@zach-ubuntu:~$ java -jar minecraft.jar
java.io.IOException: Cannot run program "javaw": 
...


Something is indeed not right: "javaw" is Microsoft's java. Equivalent to Sun/Oracle's "java".

I just tried to download and run the jar file on Lucid. It works ok. I suggest you download it again from Minecraft site.


/luigi

---

### Post by Dustout on 2011-06-07
i'm running into the same problem when i run minecraft on my ubuntu 10.10 machine

---

### Post by Rikeshar on 2011-06-08
Hey Dustout, making Sun Java the default java is what fixed it for me. Give that a try.

---

### Post by JaredFTW on 2012-07-10
> **mcduck said:**
> Try this, it's what I'm using to launch Minecraft:

java -cp /*path*/*to*/minecraft.jar net.minecraft.LauncherFrame
  Tried that, and it said: Exception in thread "main" java.lang.NoClassDefFoundError: net/minecraft/LauncherFrame
Caused by: java.lang.ClassNotFoundException: net.minecraft.LauncherFrame
at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
at java.security.AccessController.doPrivilged(Native Method)
at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
at java.lang.ClassLoader.loadClass(ClassLoader.java:266)

To make it simple:
It can't find net.minecraft.LauncherFrame, which is made when launching Minecraft. If it can't find net.minecraft.LauncherFrame, it can't launch.
To make it even simpler:
It won't launch.
:frown:

---

### Post by oldos2er on 2012-07-10
Old thread closed. Please start a new thread for your question.

---

