---
title: "Java will not run minecraft."
date: 2012-04-22
forum: General Help
---

### Post by muppetcooter on 2012-04-22
[B]I've tried right-clicking to run on OpenJDK Java 6, I've installed a JRE (into my documents, because I couldn't get it elsewhere), and I have done everything everyone has said to do.

But I get this specific error in my terminal:[/B]
> tanbam@tanbam-Presario-CQ56-Notebook-PC:~/Desktop$ java -jar minecraft.jar
java.io.IOException: Cannot run program "javaw": java.io.IOException: error=2, No such file or directory
	at java.lang.ProcessBuilder.start(ProcessBuilder.java:475)
	at net.minecraft.MinecraftLauncher.main(MinecraftLauncher.java:31)
Caused by: java.io.IOException: java.io.IOException: error=2, No such file or directory
	at java.lang.UNIXProcess.<init>(UNIXProcess.java:164)
	at java.lang.ProcessImpl.start(ProcessImpl.java:81)
	at java.lang.ProcessBuilder.start(ProcessBuilder.java:468)
	... 1 more

(java:19107): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


**And then I go into starting the game, which gives me this:**
> 27 achievements
182 recipes
Setting user: MuppetCooter, 8862232417174967031
LWJGL Version: 2.4.2
org.lwjgl.LWJGLException: X Error - disp: 0x9df9528 serial: 27 error: BadRequest (invalid request code or no such operation) request_code: 157 minor_code: 14
	at org.lwjgl.opengl.LinuxDisplay.globalErrorHandler(LinuxDisplay.java:268)
	at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
	at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:52)
	at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:684)
	at org.lwjgl.opengl.Display.create(Display.java:854)
	at org.lwjgl.opengl.Display.create(Display.java:784)
	at net.minecraft.client.Minecraft.a(SourceFile:204)
	at net.minecraft.client.Minecraft.run(SourceFile:657)
	at java.lang.Thread.run(Thread.java:679)
org.lwjgl.LWJGLException: X Error - disp: 0x9df9528 serial: 36 error: BadRequest (invalid request code or no such operation) request_code: 157 minor_code: 14
	at org.lwjgl.opengl.LinuxDisplay.globalErrorHandler(LinuxDisplay.java:268)
	at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
	at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:52)
	at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:684)
	at org.lwjgl.opengl.Display.create(Display.java:854)
	at org.lwjgl.opengl.Display.create(Display.java:784)
	at org.lwjgl.opengl.Display.create(Display.java:765)
	at net.minecraft.client.Minecraft.a(SourceFile:236)
	at net.minecraft.client.Minecraft.run(SourceFile:657)
	at java.lang.Thread.run(Thread.java:679)



**And the Minecraft Error reads as:**
> --- BEGIN ERROR REPORT 7cf3a456 --------
Generated 4/7/12 7:04 PM
 
Minecraft: Minecraft 1.2.5
OS: Linux (i386) version 3.0.0-17-generic-pae
Java: 1,6,0_23, Sun Microsystems Inc.
VM: OpenJDK Client VM (
LWJGLmixed mode, sharing), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]
 
org.lwjgl.LWJGLException: X Error - disp: 0xa2a2e98 serial: 36 error: BadRequest (invalid request code or no such operation) request_code: 157 minor_code: 14

	at org.lwjgl.opengl.LinuxDisplay.globalErrorHandler(LinuxDisplay.java:268)
	at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
	at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:52)
	at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:684)
	at org.lwjgl.opengl.Display.create(Display.java:854)
	at org.lwjgl.opengl.Display.create(Display.java:784)
	at net.minecraft.client.Minecraft.a(SourceFile:204)
	at net.minecraft.client.Minecraft.run(SourceFile:657)
	at java.lang.Thread.run(Thread.java:679)
--- END ERROR REPORT 85626c2e ----------

[b] I've exhausted all my resources and knowledge in this, and I'm at my last straw. I desperately need someone's help.

I've tried simply restarting, but that doesn't work. I have 4.7GB of memory, so it's not a memory issue.

Any suggestions anyone? Please? I desperately need help.[/b]

---

### Post by Paqman on 2012-04-22
> **muppetcooter said:**
> I've installed a JRE (into my documents, because I couldn't get it elsewhere)

When you say you've installed the JRE into your documents, do you mean you downloaded something from Oracle and dumped it there?

If so, you should always check Ubuntu Software Centre first. Open it up and install OpenJDK from it. Mojang do advise using the Oracle Java, but I've never had any problems running it with OpenJDK.

---

### Post by muppetcooter on 2012-04-22
> **Paqman said:**
> When you say you've installed the JRE into your documents, do you mean you downloaded something from Oracle and dumped it there?

If so, you should always check Ubuntu Software Centre first. Open it up and install OpenJDK from it. Mojang do advise using the Oracle Java, but I've never had any problems running it with OpenJDK.


I downloaded it from a site I believe. And it was an extractable .bin file. I can get it to open on right-click now, but the JRE problem still occurs. The runtime isn't working.
Is there any other JRE that you recommend I try downloading, or method of approaching it?

---

### Post by Paqman on 2012-04-22
> **muppetcooter said:**
> 
Is there any other JRE that you recommend I try downloading, or method of approaching it?

Yes, go to Ubuntu Software Centre and install OpenJDK. On Linux you generally don't install software by downloading it from a website, you get it from the repositories through a tool like Software Centre.

---

### Post by Hungry Man on 2012-04-22
Getting Minecraft to work is a pain in the ***. I could never get it to.

---

### Post by muppetcooter on 2012-04-22
> **Paqman said:**
> Yes, go to Ubuntu Software Centre and install OpenJDK. On Linux you generally don't install software by downloading it from a website, you get it from the repositories through a tool like Software Centre.

I have OpenJDK 6 from the Ubuntu Software Centre. I already said that in my first post.

---

### Post by efflandt on 2012-04-22
I run minecraft in 64-bit 11.10 regularly using the default openjdk installed as part of ubuntu-restricted-extras.

dpkg-query -l openjdk*
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                        Version                     Description
+++-===========================-===========================-======================================================================
un  openjdk-6-dbg               <none>                      (no description available)
un  openjdk-6-demo              <none>                      (no description available)
un  openjdk-6-doc               <none>                      (no description available)
un  openjdk-6-jdk               <none>                      (no description available)
ii  openjdk-6-jre               6b23~pre11-0ubuntu1.11.10.2 OpenJDK Java runtime, using Hotspot JIT
ii  openjdk-6-jre-headless      6b23~pre11-0ubuntu1.11.10.2 OpenJDK Java runtime, using Hotspot JIT (headless)
ii  openjdk-6-jre-lib           6b23~pre11-0ubuntu1.11.10.2 OpenJDK Java runtime (architecture independent libraries)
un  openjdk-6-jre-zero          <none>                      (no description available)
un  openjdk-6-source            <none>                      (no description available)
un  openjdk-7-jre               <none>                      (no description available)
```I never could get it to work simply trying to launch it with java.  However, there is one mistake in the command line recommended on minecraft net:

```
java -Xmx1024M -Xms512M -cp Minecraft.jar net.minecraft.LauncherFrame
```Linux is case sensitive, so it is not Minecraft.jar, it is **minecraft.jar**.  And since MC 1.2 more RAM may work better, so I use this script to launch it (which is in ~/bin, which is automatically in your PATH if you add that directory, logout, and log back in, and give any scripts execute permission):

```
#!/bin/sh
# Change cd line to your path to orig minecraft.jar with launcher, NOT ~/.minecraft/bin
cd ~/MC-client
java -Xmx2G -Xms2G -cp minecraft.jar net.minecraft.LauncherFrame
```Then if you are using Unity, you can search for **main menu** in Dash, add a laucher in terminal for the script, and once you run that launcher, you can add the launcher to the Unity bar.

If you need an icon for the launcher, use the file manager to open an original minecraft.jar (launcher, not the one in ~/.minecraft/bin) and under net/minecraft copy favicon.png somewhere (like to ~/Pictures) and rename it minecraft.png.

One other note is that minecraft movement keys may occasionally stick on when using lwjgl 2.4.2 (press same stuck key to release it, not opposite direction), so I am using lwjgl 2.6, but I don't have an explanation handy about how to put those files into several directories in ~/.minecraft

---

### Post by Paqman on 2012-04-22
> **efflandt said:**
> I never could get it to work simply trying to launch it with java.

That's the way I've always done it, I just click on the minecraft.jar and it works every time. I've got OpenJDK on 64-bit.

Muppetcooter: are you saying that you can launch Minecraft, but it crashes when you try to start a game?

---

### Post by muppetcooter on 2012-04-22
> **efflandt said:**
> I run minecraft in 64-bit 11.10 regularly using the default openjdk installed as part of ubuntu-restricted-extras.

dpkg-query -l openjdk*
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                        Version                     Description
+++-===========================-===========================-======================================================================
un  openjdk-6-dbg               <none>                      (no description available)
un  openjdk-6-demo              <none>                      (no description available)
un  openjdk-6-doc               <none>                      (no description available)
un  openjdk-6-jdk               <none>                      (no description available)
ii  openjdk-6-jre               6b23~pre11-0ubuntu1.11.10.2 OpenJDK Java runtime, using Hotspot JIT
ii  openjdk-6-jre-headless      6b23~pre11-0ubuntu1.11.10.2 OpenJDK Java runtime, using Hotspot JIT (headless)
ii  openjdk-6-jre-lib           6b23~pre11-0ubuntu1.11.10.2 OpenJDK Java runtime (architecture independent libraries)
un  openjdk-6-jre-zero          <none>                      (no description available)
un  openjdk-6-source            <none>                      (no description available)
un  openjdk-7-jre               <none>                      (no description available)
```I never could get it to work simply trying to launch it with java.  However, there is one mistake in the command line recommended on minecraft net:

```
java -Xmx1024M -Xms512M -cp Minecraft.jar net.minecraft.LauncherFrame
```Linux is case sensitive, so it is not Minecraft.jar, it is **minecraft.jar**.  And since MC 1.2 more RAM may work better, so I use this script to launch it (which is in ~/bin, which is automatically in your PATH if you add that directory, logout, and log back in, and give any scripts execute permission):

```
#!/bin/sh
# Change cd line to your path to orig minecraft.jar with launcher, NOT ~/.minecraft/bin
cd ~/MC-client
java -Xmx2G -Xms2G -cp minecraft.jar net.minecraft.LauncherFrame
```Then if you are using Unity, you can search for **main menu** in Dash, add a laucher in terminal for the script, and once you run that launcher, you can add the launcher to the Unity bar.

If you need an icon for the launcher, use the file manager to open an original minecraft.jar (launcher, not the one in ~/.minecraft/bin) and under net/minecraft copy favicon.png somewhere (like to ~/Pictures) and rename it minecraft.png.

One other note is that minecraft movement keys may occasionally stick on when using lwjgl 2.4.2 (press same stuck key to release it, not opposite direction), so I am using lwjgl 2.6, but I don't have an explanation handy about how to put those files into several directories in ~/.minecraft

Thank you very much for your response.

I tried executing it through terminal using the corrected code, and it launched properly, but the game still gives the same error code. :/

---

### Post by Becarem on 2012-07-11
sorry, delete

---

