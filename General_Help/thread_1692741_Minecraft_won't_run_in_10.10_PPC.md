---
title: "Minecraft won't run in 10.10 PPC"
date: 2011-02-21
forum: General Help
---

### Post by sciberdude on 2011-02-21
I have looked around almost everywhere for a way to run Minecraft on my PowerPC with Maverick, but nothing seems to be working. I'm not sure if it's a problem with getting Java on here (which I can't seem to do without it saying you have to have some other Java file there, or something) or a problem with liblwjgl.so (which is apparently not compiled correctly for PPCs). If anyone has the same problem or knows how to fix it, help me out here!

EDIT: I'll be gone till 9:00 (Pacific Coast Time), so I'll answer questions there.

---

### Post by sciberdude on 2011-05-09
THE FORCE OF THIS BUMP SHATTERS THE SPACE-TIME CONTINUUM

On a serious note, my laptop's battery quit charging, but, for some reason, I tried it again just now and it worked. So, problem still persists. To recap my (admittedly hard to understand) earlier post:

I'm running Ubuntu 10.10 Community-Made PPC edition, and want to open Minecraft. However, the problem is that lwjgl.so (a library for the game) is not compiled for PPC, even though it says it is compatable. Therefore, I cannot run it. On another note, I also might like the idea of using this computer as a server for Minecraft, seeing as it has 4x the ram, but the processing power of a loaf of bread. If the server software can run independently from the game, then I wouldn't mind playing it on my desktop and not dealing with it here.

Either way, I need help. Especially if someone has a link to a PPC-compatable lwjgl.so file.

---

### Post by 3rdalbum on 2011-05-09
My understanding is that the official Java doesn't work on Linux for PowerPC, and Minecraft doesn't work on any unofficial Java implementations. That would be your main problem there and I can't think of any way of working around it.

---

### Post by sqqop on 2011-08-16
I haven't had an issue with Java so much as LWJGL's assumption that all PPCs are running OSX.  I haven't found a way to properly compile it for Linux/PPC.

Maybe the LWJGL people will look into it if we all ask nicely. ;)

---

### Post by just1m on 2013-03-10
You're right. Sun/oracle and OpenJDK for Ubuntu PowerPC don't work well with minecraft. However a friend of mine and I were able to get IBM Java 64bit install on my powermac g5 dual core and our server is running both cores at less than 12% using 4 gigs of ram. No hiccups, no lag.

---

