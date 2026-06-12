---
title: "Windows emulator?"
date: 2009-12-18
forum: General Help
---

### Post by DJ . on 2009-12-18
Need a free windows emulator that can run a lot of programs. Any suggestions?

---

### Post by Shibblet on 2009-12-18
Wine is a Windows compatibility layer for Linux, it's in the repositories.  With Wine, you can run most windows programs right in Linux.

Or download VirtualBox, from Sun.  It creates a "Virtual" computer inside your existing OS.  You can install Windows in a virtual machine and run your programs there.

If you're running games, use Wine.

---

### Post by abyrne on 2009-12-18
check out the WINE project (winehq.org). I'm not exactly sure what you mean by "windows emulator", but WINE should fit your bill

---

### Post by tech newbie on 2009-12-18
What do you mean by windows emulator???
WINE runs most (not all) .exe files on linux, 
[http://www.winehq.org/](http://www.winehq.org/)

---

### Post by Cheesemill on 2009-12-18
I don't think there are any, Microsoft wouldn't let anyone use their code like that.
As mentioned you can either run Windows in a VM  (if you have the correct license and install disc) or use the compatibility layer called Wine (which works for some programs).

---

### Post by Extract_Here on 2009-12-18
Virtual box is nice but you need a windows cd to actually install it in its own mini computer. wine stands for wine is not a windows emulator although it kind of is it works nicely but not in large sizes. vmware is great but it will cost you. Cedega is a distro that is 14 dollars that will let you run native wondows games on linux.

---

### Post by USB_NL on 2009-12-18
> **DJ . said:**
> Need a free windows emulator that can run a lot of programs. Any suggestions?

wine

---

### Post by akoskm on 2009-12-18
Wine (**W**ine **I**s **N**ot an **E**mulator) is for you. I'm using it about 3 years now for several windows applications - mostly games - and it's working fine.

---

### Post by Cheesemill on 2009-12-18
> **Extract_Here said:**
> vmware is great but it will cost you

Nope. VMware Server is free.

---

### Post by coffeeandlinux on 2009-12-18
I use WINE when i just need a program here and there but I prefer VMware if I need actual windows system functions.

---

### Post by blueridgedog on 2009-12-18
Given the massive amount of information on the web and on the forum regarding running windows applications under Linux, can you advise us as to what you have considered and rejected so we don't spend time repeating the research you have done? 

I would start by reading up on wine:

[http://www.winehq.org/](http://www.winehq.org/)

If your applications don't work in wine, then we can try a different approach.  I personally keep a vertual machine for most versions of windows just so I can do tech support for those with windows from time to time (click here, open that sort of thing).

---

### Post by DJ . on 2009-12-19
Most of you are suggesting wine so I tried it out and its really buggy but works. thanks. Next I'm going to try vmware.

---

### Post by akoskm on 2009-12-19
> **DJ . said:**
> Most of you are suggesting wine so I tried it out and its really buggy but works. hanks. Next I'm going to try vmware.

Really buggy? Can you explain these bugs?

---

### Post by HighCommander540 on 2009-12-19
> **DJ . said:**
> Most of you are suggesting wine so I tried it out and its really buggy but works. hanks. Next I'm going to try vmware.

Yeah, seriously. Wine is usually not buggy unless you are trying to play an unsupported game.

I actually use both. Just for my family on VMWare though. Because they are computer stupid and can't use Ubuntu.

---

### Post by Primefalcon on 2009-12-19
> **HighCommander540 said:**
> Yeah, seriously. Wine is usually not buggy unless you are trying to play an unsupported game.

I actually use both. Just for my family on VMWare though. Because they are computer stupid and can't use Ubuntu.
Wine for most stuff, and some of the tricky stuff like ms office 2007 playonlinux is handy...

if you have stuff that you really ned and are willing to pay a small fee crossover office or crossover games is good

---

### Post by DJ . on 2009-12-19
Vmware costs money, and wine doesn't work too well. Any other FREE ones?

---

### Post by blueridgedog on 2009-12-19
Vmware is free for personal use.  What are you seeing that implies that it costs?

---

### Post by 3rdalbum on 2009-12-20
> **DJ . said:**
> Vmware costs money, and wine doesn't work too well. Any other FREE ones?

Vmware is not a Windows emulator. It's a virtualisation system; you can run an operating system on top of your existing one.

You can try Virtualbox if you want to run Windows on top of Linux.

Crossover have a 15 day demo of their product (which is based on Wine code); you can give that a try, and if it works well enough for what you want you can buy it.

Wine is the only software that's free and does not require you to run Windows.

---

### Post by llamabr on 2009-12-20
> **DJ . said:**
> Vmware costs money, and wine doesn't work too well. Any other FREE ones?

Wine is almost never the correct answer.  As many have noted, it's buggy, it runs many, but not most ms apps, and it's likely to crash on you.  Instead, tell us what programs you're trying to run.  There is very likely a native application that does what you're trying to do.

---

### Post by MelDJ on 2009-12-20
virtualbox

---

### Post by blueridgedog on 2009-12-20
What applications do you need to run?  Perhaps we can help tweak wine to run them or we can suggest alternative Linux applications.  I used wine initially for a few specific applications, but have since learned their Linux replacements.

---

### Post by Yogotiss on 2009-12-20
Download the latest and greatest "Play On Linux"
[http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html)
Be sure to install the missing packages from synaptic if needed.

---

