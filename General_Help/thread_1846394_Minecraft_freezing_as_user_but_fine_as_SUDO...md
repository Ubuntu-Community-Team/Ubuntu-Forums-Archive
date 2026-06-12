---
title: "Minecraft freezing as user but fine as SUDO.."
date: 2011-09-18
forum: General Help
---

### Post by tnkie on 2011-09-18
I am using minecraft 1.8.1, after world generation the game freezes I  can see the minecraft quick-bar and cursor but everything else is black  for about 30 seconds. After this the game resumes as normal for a short  amount of time until it freezes, and the cycle repeats.

**When I run Minecraft using sudo I get none of these problems**, but this of course isn't the preferred method due to security concerns.

Thanks in advance! 						 						
```

spayde@miencraft:~/Desktop$ java -Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame
17 achievements
161 recipes
Setting user: spayde, -4823106388814997630
Loading: net.java.games.input.LinuxEnvironmentPlugin
Failed to open device (/dev/input/event10): Failed to open device /dev/input/event10 (13)

Failed to open device (/dev/input/event9): Failed to open device /dev/input/event9 (13)

Failed to open device (/dev/input/event8): Failed to open device /dev/input/event8 (13)

Failed to open device (/dev/input/event7): Failed to open device /dev/input/event7 (13)

Failed to open device (/dev/input/event6): Failed to open device /dev/input/event6 (13)

Failed to open device (/dev/input/event5): Failed to open device /dev/input/event5 (13)

Failed to open device (/dev/input/event4): Failed to open device /dev/input/event4 (13)

Failed to open device (/dev/input/event3): Failed to open device /dev/input/event3 (13)

Failed to open device (/dev/input/event2): Failed to open device /dev/input/event2 (13)

Failed to open device (/dev/input/event1): Failed to open device /dev/input/event1 (13)

Failed to open device (/dev/input/event0): Failed to open device /dev/input/event0 (13)

Linux plugin claims to have found 0 controllers

Starting up SoundSystem...
Initializing LWJGL OpenAL
    (The LWJGL binding of OpenAL.  For more information, see http://www.lwjgl.org)
OpenAL initialized.

Wrong location! bx@57
java.lang.Exception: Stack trace
        at java.lang.Thread.dumpStack(Thread.java:1249)
        at vy.a(SourceFile:471)
        at lb.a(SourceFile:177)
        at gd.a(SourceFile:42)
        at ic.e(SourceFile:97)
        at ic.c(SourceFile:57)
        at ic.b(SourceFile:86)
        at rv.c(SourceFile:319)
        at rv.a(SourceFile:276)
        at net.minecraft.client.Minecraft.d(SourceFile:1654)
        at net.minecraft.client.Minecraft.a(SourceFile:1563)
        at net.minecraft.client.Minecraft.a(SourceFile:1527)
        at net.minecraft.client.Minecraft.a(SourceFile:1447)
        at jv.c(SourceFile:161)
        at jv.a(SourceFile:119)
        at qr.a(SourceFile:72)
        at qr.f(SourceFile:120)
        at qr.i(SourceFile:108)
        at net.minecraft.client.Minecraft.k(SourceFile:1197)
        at net.minecraft.client.Minecraft.run(SourceFile:666)
        at java.lang.Thread.run(Thread.java:662)
Chunk file at 18,20 is in the wrong location; relocating. (Expected 18, 20, got 17, 21)
New max size: 484
New max size: 784
New max size: 1444
New max size: 4096
New max size: 4356
Placed stronghold in INVALID biome at (-32, -42)
Placed stronghold in INVALID biome at (61, -7)
java.io.IOException: Input/output error
        at java.io.RandomAccessFile.write(Native Method)
        at java.io.RandomAccessFile.writeInt(RandomAccessFile.java:986)
        at jc.a(SourceFile:343)
        at jc.a(SourceFile:279)
        at tu.close(SourceFile:259)
        at java.util.zip.DeflaterOutputStream.close(DeflaterOutputStream.java:149)
        at java.io.FilterOutputStream.close(FilterOutputStream.java:143)
        at gd.a(SourceFile:64)
        at ic.b(SourceFile:121)
        at ic.a(SourceFile:146)
        at rv.a(SourceFile:254)
        at rv.c(SourceFile:1649)
        at net.minecraft.client.Minecraft.k(SourceFile:1388)
        at net.minecraft.client.Minecraft.run(SourceFile:666)
        at java.lang.Thread.run(Thread.java:662)
Stopping!

SoundSystem shutting down...
    Author: Paul Lamb, www.paulscode.com
```

---

### Post by tnkie on 2011-09-19
Bump.

---

### Post by forcemaker on 2011-09-22
I have the same problem.

---

### Post by NERDMAN! on 2011-09-22
although ive never had this issue before i did once have something similar.
i would first suggest a total clean reinstall of minecraft. you can do this by going to your home directory, enabling the display of hidden files (ctrl H) finding .minecraft and deleting it, then running the games executable jar file.

if this fails i would suggest reinstalling java. on that note which version of java are you using? sun jvm 6 update 27? or openjdk from the software center?

---

