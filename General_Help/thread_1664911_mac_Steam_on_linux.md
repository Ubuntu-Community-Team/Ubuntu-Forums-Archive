---
title: "mac Steam on linux"
date: 2011-01-11
forum: General Help
---

### Post by Dutch-Man on 2011-01-11
Hi,

I was wondering since there is a MAC version of steam we might could run it on our linux computers. Because the steam version uses OpenGL. The reason that i am asking this is that steam+Wine just hates me. And since its the both based on Unix kernel. And Ubuntu is based on Debian same as Mac (with heavy modifications).

Is this a possible thing to manage?

---

### Post by Joe of loath on 2011-01-11
Errr, where are you getting this info from?

Ubuntu runs the Linux kernel, mac runs the Darwin UNIX kernel. Ubuntu is based on Debian, Mac is based loosely on NEXTstep and FreeBSD I believe.

Pretty much the only things that run on both are command line programs installed from source. Binaries like steam aren't compatible, as the mac kernel is so different, and mac OS has its own application API.

---

### Post by ean5533 on 2011-01-11
The Mac kernel and the Linux kernel both have the same ancestor (UNIX), but that doesn't mean that applications are compatible or easy to port. As Joe mentioned, several basic command-line programs exist in both worlds, but any GUI program like Steam is going to require a dedicated port. As of right now, such a port does not exist. It is easier to get the Windows version working via Wine than it would be to try and get the Mac version working.

Hopefully Valve is secretly working on a native Linux port of Steam, but I doubt it's coming any time soon.

---

### Post by lovinglinux on 2011-01-11
Install Steam using [PlayOnLinux]("http://www.playonlinux.com/"). It works flawlessly for me on Ubuntu 10.04 32bit. Seriously, it works incredibly well. It is also listed as [Platinum on WineDB]("http://appdb.winehq.org/").

---

### Post by Dutch-Man on 2011-01-11
Oh wait. I always get those 2 distos wrong :P But i can explain my problem. I am running ubuntu 10.10 and PinGuyOS 10.10.1(ubuntu remastered) If i use play on linux i cant the ingame people and weapons. When i use the steam client itself the text is screwed(i have the windows fonts). And on both ways i get a fullscreen problem that my screen starts to flicker. In Windows i dont have any of this things. And thats the only reason i still have it.

---

### Post by mdshann on 2011-01-11
What game are you trying to run? That may have more to do with it than steam.

---

### Post by Dutch-Man on 2011-01-12
I want to play CSS.

---

### Post by ean5533 on 2011-01-12
I'm assuming you're talking about Counter Strike: Source. If so, I'd recommend reading through [this page]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731") for tips to get it working.

---

### Post by Dutch-Man on 2011-01-12
Oh thanks i see why i dont see the models. I need to disable GLSL. But how do i do that?

---

### Post by ean5533 on 2011-01-12
No idea. A quick google search brought up this:

[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

It looks like GLSL can be disabled by following instructions on that page, but I haven't tried so I can't confirm.

---

