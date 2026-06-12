---
title: "Annoyance : ATI + OpenGL + Minecraft"
date: 2011-01-11
forum: General Help
---

### Post by waspbloke on 2011-01-11
I have this problem that I can't make go away.

Basically, I can only get Minecraft to work if I run the xrandr_cycle in the Video tests section of System Testing utility ( System > Administration > System Testing ). However, doing this causes my fan to kick in shortly after completion and does not switch off - usually ubuntu will idle away happily cool and I hardly ever hear the fan. Once I start to play Minecraft, the heat build up will cause the game graphics to lag and stutter badly after about an hour or so and only a shutdown and cooling off period will do.

If I try to play Minecraft without running the xrandr_cycle I get the Minecraft login but after that just a black window with this in the console:
```
	at net.minecraft.client.Minecraft.a(SourceFile:231)
	at net.minecraft.client.Minecraft.run(SourceFile:641)
	at java.lang.Thread.run(Thread.java:662)
Caused by: java.lang.ArrayIndexOutOfBoundsException: 0
	at org.lwjgl.opengl.XRandR$Screen.<init>(XRandR.java:234)
	at org.lwjgl.opengl.XRandR$Screen.<init>(XRandR.java:196)
	at org.lwjgl.opengl.XRandR.populate(XRandR.java:87)
	at org.lwjgl.opengl.XRandR.access$100(XRandR.java:52)
	at org.lwjgl.opengl.XRandR$1.run(XRandR.java:110)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.lwjgl.opengl.XRandR.getConfiguration(XRandR.java:108)
	at org.lwjgl.opengl.LinuxDisplay.init(LinuxDisplay.java:618)
	at org.lwjgl.opengl.Display.<clinit>(Display.java:135)
```

Running Minecraft as su doesn't do it either, still need to do the xrandr_cycle.

Other OpenGL applications work fine (3D Chess, Google Earth, Blender).

The xrandr_cycle I understand just tests all the supported resolutions of the connected display device. I have a Dell Studio XPS 1640 laptop with 512MB ATI RADEON HD 3670 + ATI Fire GL drivers, output over HDMI to a 32" LED TV @ 1920x1080. The laptop display is disabled, but disconnecting the HDMI and using the native display does not correct the problem.

Can anybody shed some light on how to get around this problem without using the System [S]Cooker[/S] Testing utility?

---

