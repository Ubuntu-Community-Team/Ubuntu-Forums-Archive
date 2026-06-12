---
title: "Java on Ubuntu ARM"
date: 2012-06-21
forum: General Help
---

### Post by MrWeaver on 2012-06-21
Hey guys, I'm not sure where else to put this! I could not see a section for Java or Arm, but if I just missed it please move me!

The .jar in question is Minecraft. I'm trying to run Minecraft under Ubuntu ARM, but I can't get into Minecraft.jar.

> root@localhost:/# java -jar minecraft.jar

java.io.IOException: Cannot run program "javaw": java.io.IOException: error=2, No such file or directory
at java.lang.ProcessBuilder.start(ProcessBuilder.java:475)
at net.minecraft.MinecraftLauncher.main(MinecraftLauncher.java:31)
Caused by: java.io.IOException: java.io.IOException: error=2, No such file or directory
at java.lang.UNIXProcess.<init>(UNIXProcess.java:164)
at java.lang.ProcessImpl.start(ProcessImpl.java:81)
at java.lang.ProcessBuilder.start(ProcessBuilder.java:468)
... 1 more


Where the java version I'm using is

> root@localhost:/# java -version

java version "1.6.0_18"
IcedTea6 Runtime Environment (1.8.13) (6b18-1.8.13-0ubuntu1~10.10.1)
OpenJDK Zero VM (build 14.0-b16, mixed mode)


Firstly, I don't know why this displays "IcedTea6 Runtime Environment". It is not installed, while OpenJDK-6 JRE is. I thought the way to change this is "update-alternatives --config java" but there are no alternatives, just OpenJDK.

So the obvious thing would be that I need Sun Java. However, my other linux machine (AMD64) runs great, on OpenJDK. Here, java -version gives me

> iain@curie:~$ java -version

java version "1.6.0_24"
OpenJDK Runtime Environment (IcedTea6 1.11.1) (6b24-1.11.1-4ubuntu3)
OpenJDK 64-Bit Server VM (build 20.0-b12, mixed mode)


I've seen several people point out javaw is some Windows version, and the .jar must be the wrong version but that's not it. Any thoughts chaps? The "javaw" problem seems to crop up a fair bit, and the answer is commonly "use Sun's Java". I'd like to avoid opening that can of worms if possible. If that's my best shot though, I have the files from Sun from [http://www.oracle.com/technetwork/java/embedded/overview/getstarted/index.html?origref=http://www.oracle.com/technetwork/java/javase/downloads/embedded-jsp-135769.html]("http://www.oracle.com/technetwork/java/embedded/overview/getstarted/index.html?origref=http://www.oracle.com/technetwork/java/javase/downloads/embedded-jsp-135769.html"). I'd still need some help installing and linking these correctly.

---

### Post by SergioFern on 2012-07-19
I am also trying to run Minecraft on Ubuntu ARM, and you don't need Sun Java. OpenJDK6 works fine on an x86 installation. What I think we need is an arm port of one or maybe most of the contents of the Minecraft jar. I replaced several with ones I could find and I'm getting errors still. I'll provide links with the files you need if i can get it working, but there is interest in this.

---

