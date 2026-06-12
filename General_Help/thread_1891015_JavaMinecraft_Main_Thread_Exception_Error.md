---
title: "Java/Minecraft Main Thread Exception Error"
date: 2011-12-04
forum: General Help
---

### Post by DaimyoKirby on 2011-12-04
I just installed Oracle JRE 7, and set it to the default using [these instructions]("http://askubuntu.com/questions/56104/how-can-i-install-oracle-jre-7").

When I opened minecraft, it black-screened, so I ran it in terminal, and it turned up the following error:
```
Exception in thread "Minecraft main thread" java.lang.UnsatisfiedLinkError: /home/alden/.minecraft/bin/natives/liblwjgl.so: /home/alden/.minecraft/bin/natives/liblwjgl.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
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
	at net.minecraft.client.Minecraft.a(SourceFile:187)
	at net.minecraft.client.Minecraft.run(SourceFile:644)
	at java.lang.Thread.run(Unknown Source)
```
I don't know if it matters, but when I was installing the mozilla/chrome plugin, I changed "/i386" to "amd64"; should it have been "x64" instead?

Can anyone tell me what I did wrong?

---

### Post by oldtimer7777 on 2011-12-04
I don't prefer those instructions to get it working with Minecraft... Better would be:

[https://debianhelp.wordpress.com/2011/11/13/how-to-install-sun-java-se-1-7/](https://debianhelp.wordpress.com/2011/11/13/how-to-install-sun-java-se-1-7/)

> **DaimyoKirby said:**
> I just installed Oracle JRE 7, and set it to the default using [these instructions]("http://askubuntu.com/questions/56104/how-can-i-install-oracle-jre-7").

When I opened minecraft, it black-screened, so I ran it in terminal, and it turned up the following error:
```
Exception in thread "Minecraft main thread" java.lang.UnsatisfiedLinkError: /home/alden/.minecraft/bin/natives/liblwjgl.so: /home/alden/.minecraft/bin/natives/liblwjgl.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
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
    at net.minecraft.client.Minecraft.a(SourceFile:187)
    at net.minecraft.client.Minecraft.run(SourceFile:644)
    at java.lang.Thread.run(Unknown Source)
```I don't know if it matters, but when I was installing the mozilla/chrome plugin, I changed "/i386" to "amd64"; should it have been "x64" instead?

Can anyone tell me what I did wrong?

---

### Post by DaimyoKirby on 2011-12-04
But aren't those instructions for the Development Kit, and not the runtime environment?

---

### Post by oldtimer7777 on 2011-12-04
> **DaimyoKirby said:**
> But aren't those instructions for the Development Kit, and not the runtime environment?

They are one in the same. Do it. It is what I use to play Minecraft with Java 1.7 like you apparently wish to do. :)

AskUbuntu just sucks sometimes when it comes to actually tested and working instructions.  fyi

---

### Post by DaimyoKirby on 2011-12-04
> **oldtimer7777 said:**
> They are one in the same. Do it.

Oh. Ok, I'll give it a shot and report back what happens.

---

### Post by oldtimer7777 on 2011-12-04
> **DaimyoKirby said:**
> Oh. Ok, I'll give it a shot and report back what happens.

Please report back here to let us know your success.  Thanks.

---

### Post by DaimyoKirby on 2011-12-04
Well, I followed those instructions to the letter, and I'm getting what appears to be the same error:
```

Exception in thread "Minecraft main thread" java.lang.UnsatisfiedLinkError: /home/alden/.minecraft/bin/natives/liblwjgl.so: /home/alden/.minecraft/bin/natives/liblwjgl.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
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
	at net.minecraft.client.Minecraft.a(SourceFile:187)
	at net.minecraft.client.Minecraft.run(SourceFile:644)
	at java.lang.Thread.run(Unknown Source)

```

Also, in chrome, the plugin says it needs some critical security updates, and has a link.

**EDIT:** Oh, and to test this, I've been running in terminal *java -jar minecraft.jar*

---

### Post by oldtimer7777 on 2011-12-04
That's strange..    Have you tried rolling back to JRE 1.6 from the PPA? 

> **DaimyoKirby said:**
> Well, I followed those instructions to the letter, and I'm getting what appears to be the same error:
```

Exception in thread "Minecraft main thread" java.lang.UnsatisfiedLinkError: /home/alden/.minecraft/bin/natives/liblwjgl.so: /home/alden/.minecraft/bin/natives/liblwjgl.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
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
    at net.minecraft.client.Minecraft.a(SourceFile:187)
    at net.minecraft.client.Minecraft.run(SourceFile:644)
    at java.lang.Thread.run(Unknown Source)

```Also, in chrome, the plugin says it needs some critical security updates, and has a link.

**EDIT:** Oh, and to test this, I've been running in terminal *java -jar minecraft.jar*

---

### Post by DaimyoKirby on 2011-12-04
I probably will now. I was running java 6, but I wanted to use a mod, and it said it would work if I updated to oracle 7, so I suppose I'll just forget about that.
Thanks for your help.

---

### Post by oldtimer7777 on 2011-12-04
> **DaimyoKirby said:**
> I probably will now. I was running java 6, but I wanted to use a mod, and it said it would work if I updated to oracle 7, so I suppose I'll just forget about that.
Thanks for your help.

I want to see if it will still work..  JRE 1.7 installed and works great on my 11.10 64-bit system...  Are you sure you using the right version for your architecture, either 32-bit or 64-bit?? Something must be fundamentally wrong.

---

### Post by DaimyoKirby on 2011-12-04
I'm running 64-bit Xubuntu 11.10.
I downloaded the 64-bit tar.gz file.
I used the 64-bit commands in those instructions (when presented the choice).
I honestly don't know either what I'm doing wrong, but it's probably me.
Do you know of a way to purge old versions of java? I seem to have old 1.6 and 1.7 versions hanging around, from all the different ways and times I've tried to install java...

---

### Post by oldtimer7777 on 2011-12-04
> **DaimyoKirby said:**
> I'm running 64-bit Xubuntu 11.10.
I downloaded the 64-bit tar.gz file.
I used the 64-bit commands in those instructions (when presented the choice).
I honestly don't know either what I'm doing wrong, but it's probably me.
Do you know of a way to purge old versions of java? I seem to have old 1.6 and 1.7 versions hanging around, from all the different ways and times I've tried to install java...

You would need to use a PPA purge to remove whatever you installed from a PPA. 

As for the one you downloaded separately, I have know idea.

---

### Post by DaimyoKirby on 2011-12-04
Well, I did a little snooping around, and I found there were a bunch of java versions installed in the /usr/lib/jvm folder, and I cleared that out.
I tried installing oracle jdk 7 again, but it still didn't work, so I suppose I'll just go back to 6.

---

### Post by DaimyoKirby on 2012-02-13
I have since stopped using the computer that was having said problem, so I honestly can't remember why I was getting that error code.
I'm going to mark it solved so it has resolution, and is considered closed, even though it technically isn't.

Thanks for the help.

My apologies to future people who may be looking for an answer; don't lose hope, and keep searching.

---

