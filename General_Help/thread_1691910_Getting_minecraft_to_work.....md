---
title: "Getting minecraft to work...."
date: 2011-02-20
forum: General Help
---

### Post by Neur0123 on 2011-02-20
Hi!
Ive been using ubuntu 10.10 for a couple of weeks now, and im loving it, but there is still one thing that brings me back to Windows - Minecraft.

The problem is that when I try to start a new world the program crashes while "Building Terrain", no error text or anything.
Ive downloaded Sun Java 6 Runtime, and im opening it with that, but nothing!

Help me Ubuntuforums, your my only hope!

---

### Post by veggen on 2011-02-20
Does it give you any error or just crashes?

---

### Post by Neur0123 on 2011-02-21
Nothing, it just dissapears =/

---

### Post by Syed75 on 2011-02-21
Sun Java 6 Web Start

---

### Post by Neur0123 on 2011-02-21
Could you explain that a bit more please?

---

### Post by veggen on 2011-02-21
Sorry for the dumb question, but is Minecraft a desktop app? I mean, does it have a jar to start or something like that? If so, try running it from the terminal (java -jar minecraft.jar), so that you see the possible error output. 
If it's a in-browser thing, maybe try a different browser plugin or a different browser. If it's a Web Start thing, try removing all traces of all javas (sun, openJdk, what not) and install one of them again (sun java from the repo is probably the safest bet).

---

### Post by DarthScape on 2011-02-21
I find that OpenJDK works best for me, for Minecraft at least. Never had a problem.

---

### Post by Neur0123 on 2011-02-23
Ive tried with open JDK aswell and i get the same problem, only i get it a tiny bit earlier in the loading screen...

Anyway, i ran the minecraft.jar file through the terminal and got this error message:

Exception in thread "main" java.lang.NoClassDefFoundError: //download/minecraft/jar
Caused by: java.lang.ClassNotFoundException: ..download.minecraft.jar
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: ./download/minecraft.jar. Program will exit.

Which is complete jibberish to me...

---

### Post by FoxEWolf on 2011-02-23
Minecraft.................. *sigh* Why is it so popular?

The only really news I have heard on the subject was the ability to construct genitals out of gold. Explain the point of this game to me please. Wait.. I don't care. Random Rant....Over =P

Nah I just don't have the time for these kind of things.

---

### Post by Neur0123 on 2011-02-23
Well, for me its the whole creativity thing, making your own home and then expanding it. I actually think its so popular because its some kind of primal instinct to make a shelter, explore, defend you belongings, and find diamonds ;)

And I don't really think its more of a waste of time than any other game.
But of course its not for everyone.

---

### Post by WorMzy on 2011-02-23
Delete your .minecraft/bin folder (press Ctrl+H in nautilus to see hidden folders), then relaunch the game.

---

### Post by Neur0123 on 2011-02-24
That didnt help :(

---

### Post by veggen on 2011-02-26
Some people mention that downloading from
[https://s3.amazonaws.com/MinecraftDownload/classic/minecraft.jar](https://s3.amazonaws.com/MinecraftDownload/classic/minecraft.jar)
fixes the problem. If not, try these:
[http://cwraig.id.au/?p=295](http://cwraig.id.au/?p=295)
[http://www.worldofminecraft.com/node/2796](http://www.worldofminecraft.com/node/2796)

---

