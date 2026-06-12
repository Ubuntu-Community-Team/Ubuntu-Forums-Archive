---
title: "Minecraft, java, blackscreen, lwjgl"
date: 2010-09-24
forum: General Help
---

### Post by J V on 2010-09-24
Minecraft keeps crashing with an error stating a file is missing from the config folder (Which is true) - liblwjgl.so

I tried using the web-client version downloaded liblwjgl.so but then it said:
```

```

So, where would I find that specific file at that specific version?...

---

### Post by Faesin on 2010-09-24
I was having the same error, so I found this:

> 
Ran into this today, myself. After just buying the game. This seems to be a bug in the bundled version of the LWJGL library. 

What fixed it for me was downloading a nightly build of LWJGL from [here]("http://lwjgl.org/download.php") and replace all the .jar and .so files in $HOME/.minecraft/ with new versions from the nightly build.

The only (tiny) downside to this is a small bug in shadow rendering of animals and pickups/collectables.
Source: [http://www.minecraftforum.net/viewtopic.php?f=17&t=28065]("http://[URL")


I dont really know how to fix it (since I am a newb) but I did what he said and managed to resolve it, but only to stumble upon a different error. 

If you didnt purchased the game (like me), most of the thread involving the said error ends up saying that the problem was fixed with the game update.

---

### Post by J V on 2010-09-25
Every time I mess with those files I get a different error: After installing lwjgl 2.5 I get:

```
Exception in thread "Minecraft main thread" java.lang.UnsatisfiedLinkError: /home/j/.minecraft/bin/natives/liblwjgl.so: /home/j/.minecraft/bin/natives/liblwjgl.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
```In case notch started work on minecraft with lwjgl 1.x I'll try one of those just in case...

Edit: Figured it out!

Minecraft works with any 2.x version of jwjgl BUT you have to install the jars and the native BUT if you are on 64 bit you have to rename the 64bit file to look like the normal file or it won't start: BINGO!

Edit: Noooo! Now the game is constantly stuck on pause!

Edit: Latest version works but no sound :/

(Ignore if you don't play minecraft)
Omg: This map has a huge lavafall, waterfall and a cave system that goes down to adminite... Oh yeah, by the way, I haven't even made a stone pickaxe yet but I found diamond :D

---

### Post by omgitsmit on 2010-10-04
For those who want to run Minecraft straight from the JRE (not in the browser), you're going to need some library files (Mainly from the Java Monkey Engine). It took me HOURS and HOURS to find out how to get Minecraft to run on Ubuntu Linux.

Posted a great article on how i did it on my blog - [http://timashley.me/node/596](http://timashley.me/node/596)

Enjoy! :)

---

### Post by Lt Shinysides on 2010-10-04
> **J V said:**
> Every time I mess with those files I get a different error: After installing lwjgl 2.5 I get:

```
Exception in thread "Minecraft main thread" java.lang.UnsatisfiedLinkError: /home/j/.minecraft/bin/natives/liblwjgl.so: /home/j/.minecraft/bin/natives/liblwjgl.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
```In case notch started work on minecraft with lwjgl 1.x I'll try one of those just in case...

Edit: Figured it out!

Minecraft works with any 2.x version of jwjgl BUT you have to install the jars and the native BUT if you are on 64 bit you have to rename the 64bit file to look like the normal file or it won't start: BINGO!

Edit: Noooo! Now the game is constantly stuck on pause!

Edit: Latest version works but no sound :/

(Ignore if you don't play minecraft)
**Omg: This map has a huge lavafall, waterfall and a cave system that goes down to adminite... Oh yeah, by the way, I haven't even made a stone pickaxe yet but I found diamond **:D

That's just unfair :(
I've barely found *gold *with a metal pickaxe...

---

