---
title: "Need help &quot;translating&quot; java log"
date: 2012-05-29
forum: General Help
---

### Post by DaimyoKirby on 2012-05-29
Hello there. A while ago, I installed Oracle JRE 7u4, and followed some guide that told me how to correctly update it.  Afterwards, and just now, I verified that I had correctly installed it by checking both on Java.com and using "java -version" in the terminal.

I noticed that the default program set to open Minecraft is "Sun Java 6 Runtime", which, when I checked in the properties, correlates to the command "cautious-launcher".
My first question would be - does this launch it through Java 7, since that is the default, or is that still forcing Minecraft to use Java 6?

Now, when I try to run Minecraft though console, using "java -jar minecraft.jar", this is the output:
```
alden@DualCoreZorin:~/Desktop$ java -jar minecraft.jar
java.io.IOException: Cannot run program "javaw": error=2, No such file or directory
	at java.lang.ProcessBuilder.start(Unknown Source)
	at net.minecraft.MinecraftLauncher.main(MinecraftLauncher.java:31)
Caused by: java.io.IOException: error=2, No such file or directory
	at java.lang.UNIXProcess.forkAndExec(Native Method)
	at java.lang.UNIXProcess.<init>(Unknown Source)
	at java.lang.ProcessImpl.start(Unknown Source)
	... 2 more
MCPatcherUtils initialized. Directory /home/alden/.minecraft
27 achievements
182 recipes
Setting user: DaimyoKirby, 569847638993845074
Exception in thread "Minecraft main thread" java.lang.UnsatisfiedLinkError: /home/alden/.minecraft/bin/natives/liblwjgl.so: /home/alden/.minecraft/bin/natives/liblwjgl.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary1(Unknown Source)
	at java.lang.ClassLoader.loadLibrary0(Unknown Source)
	at java.lang.ClassLoader.loadLibrary(Unknown Source)
	at java.lang.Runtime.load0(Unknown Source)
	at java.lang.System.load(Unknown Source)
	at org.lwjgl.Sys$1.run(Sys.java:69)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.lwjgl.Sys.doLoadLibrary(Sys.java:65)
	at org.lwjgl.Sys.loadLibrary(Sys.java:81)
	at org.lwjgl.Sys.<clinit>(Sys.java:98)
	at org.lwjgl.opengl.Display.<clinit>(Display.java:132)
	at net.minecraft.client.Minecraft.an(Unknown Source)
	at net.minecraft.client.Minecraft.run(Unknown Source)
	at java.lang.Thread.run(Unknown Source)
```
When I run that command, it loads the launcher, stopping at the line before "27 achievements" in the terminal. Then, when I log in, it starts writing everything else that I pasted above. And then it just hangs on a black screen.

My next question - what does this mean?

---

