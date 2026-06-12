---
title: "Linux Gaming?"
date: 2009-09-12
forum: General Help
---

### Post by GroogFish on 2009-09-12
So I just found that one of my favorite games of all time, Savage 2, is available for Linux (yay!). I do have it on my windows partition but I know that Linux is good at optimizing things so I'm hoping the game will run faster on Linux then on windows. But I have a few questions about Linux because since I use it for everything but gaming I haven't needed to worry about my system resources or optimization (everything just runs fast).

1. On Windows a lot of background programs slow down the computer when playing games, so I've had to disable them. Will Linux have a similar problem? 

2. On Windows I've adjusted everything for best performance, including the gui and keeping everything cleaned out and defragged. Do I have to worry about this in Linux?

3. Will my desktop run in the background like Windows desktop does (I stupid idea on Microsoft's part)? I'm using things like compzis, awm, and lots of appearance affects. Do these need to be disabled or is Linux smart enough to ignore them when they aren't in use? (Windows fails to do this).

4. I've heard that compiling things on your own will greatly affect the speed of games. Is there any web tutorials where I can read up on this? I'm pretty new to Linux.

Thanks for any help I might receive :D

---

### Post by Ms_Angel_D on 2009-09-12
You never know until you try ;)

---

### Post by Mike_IronFist on 2009-09-12
> **GroogFish said:**
> So I just found that one of my favorite games of all time, Savage 2, is available for Linux (yay!). I do have it on my windows partition but I know that Linux is good at optimizing things so I'm hoping the game will run faster on Linux then on windows. But I have a few questions about Linux because since I use it for everything but gaming I haven't needed to worry about my system resources or optimization (everything just runs fast).

1. On Windows a lot of background programs slow down the computer when playing games, so I've had to disable them. Will Linux have a similar problem? 

2. On Windows I've adjusted everything for best performance, including the gui and keeping everything cleaned out and defragged. Do I have to worry about this in Linux?

3. Will my desktop run in the background like Windows desktop does (I stupid idea on Microsoft's part)? I'm using things like compzis, awm, and lots of appearance affects. Do these need to be disabled or is Linux smart enough to ignore them when they aren't in use? (Windows fails to do this).

4. I've heard that compiling things on your own will greatly affect the speed of games. Is there any web tutorials where I can read up on this? I'm pretty new to Linux.

Thanks for any help I might receive :D

All excellently reasonable questions.

1. Absolutely not, Linux runs little, if anything, in the background most of the time. Your RAM will not get eaten up, nor will your CPU cycles, by background programs, because Linux doesn't rely on them like that.

2. Not necessarily, depending on your current setup. Please post some system specs for more details.

3. The GNOME desktop doesn't "run" quite like Windows explorer does. The desktop itself is more of a frontend to a command line. It's a GUI for the terminal and puts little, if any, stress on your processor or RAM.

4. Compiling a game configures it exactly for your system, meaning it's set up to run "perfectly" for your machine. However, compiling stuff can be slow and usually doesn't yield much better results.

---

### Post by shae on 2009-09-12
1.  There are background processes and such in Linux, but there are major differences in the design of Linux and Windows.  These processes are not going to drastically decrease your games' performance.

2.  These things are not issues in Linux.

3.  Yes, using desktop effects can degrade graphics performance due to some weaknesses in Xorg, turning off effects is easy to do while you game.  Hopefully, this issue will be fixed in a future release of Xorg.

4.  Compiling things will increase only certain tasks.  Anything that can make use of SEE(2,3,4) or MMX can benifit, but usually things like media encoders benifit the most.  Usually it is not worth the time to compile.

5.  You should check to see that the games you want to play have either Linux native clients or can run in Wine.

6.  You should consider dual booting since you like playing Games.

---

### Post by Mike_IronFist on 2009-09-12
> **GroogFish said:**
> 
3. Will my desktop run in the background like Windows desktop does (I stupid idea on Microsoft's part)? I'm using things like compzis, awm, and lots of appearance affects. Do these need to be disabled or is Linux smart enough to ignore them when they aren't in use? (Windows fails to do this).


Excuse me, but I neglected to mention, programs that are not being currently run, instead of running "in the background" go to your swap partition, waiting to come on back when your computer calls on them. In addition, stuff that isn't being directly used usually doesn't take up any CPU at all. It's pretty cool.

---

### Post by GroogFish on 2009-09-12
System Specs

1.5gig RAM
3.0Ghz Integrated (Hyperthreaded) Pentium 4 Processor (32bit)
NVidia GeForce 8400gs ~ 512mb

---

### Post by CatKiller on 2009-09-12
> **GroogFish said:**
> 4. I've heard that compiling things on your own will greatly affect the speed of games.

That might well be true *if you're compiling the game itself*. Otherwise you're just tinkering at the edges.

---

### Post by P4man on 2009-09-12
> **GroogFish said:**
> 
1. On Windows a lot of background programs slow down the computer when playing games, so I've had to disable them. Will Linux have a similar problem? 

If you run lots of cpu or I/O intensive background apps, then yes, sure. Despite what everyone else say. The big difference compared to windows is that you don't need nearly as many background apps (no virus scanner to name one), and that you have 100% control over it. But if you're gonna run some folding app in the background with equal priority, your game performance will plummet just like it does on windows.

> 2. On Windows I've adjusted everything for best performance, including the gui and keeping everything cleaned out and defragged. Do I have to worry about this in Linux?

Defragging, no, you dont have to worry about that. 

```
3. Will my desktop run in the background like Windows desktop does (I stupid idea on Microsoft's part)? I'm using things like compzis, awm, and lots of appearance affects. Do these need to be disabled or is Linux smart enough to ignore them when they aren't in use? (Windows fails to do this).

```

Again, there is no fundamental difference with windows here. Your desktop manager will keep running, as it should. Compiz, Im not sure, i don't think it makes much if any difference performance wise, but it can give problems in some games. 

> 4. I've heard that compiling things on your own will greatly affect the speed of games. Is there any web tutorials where I can read up on this? I'm pretty new to Linux.


You don't want to, really :)
Unless you think you know better what compiler flags to use (which is like black magic) than whoever developed or packaged the game. In the few cases you will compile anything, you will use the standard 

./configure 
make 
sudo make install

Which compiles the app with a preset template of options. IT will give  the same result as installing a precompiled binary. Anything else will be out of your reach.

---

### Post by talsemgeest on 2009-09-12
What you said about a game running better under Linux than it did under Windows is probably not going to be true. The main problem is that the Hardware manufacturers put more money into the windows drivers, and very little into the Linux drivers, so you are more likely to get better performance (more FPS, etc...) under Windows than Linux. However, the difference should be negligible, and the game should be more than playable.

---

### Post by CatKiller on 2009-09-12
> **talsemgeest said:**
> What you said about a game running better under Linux than it did under Windows is probably not going to be true. 

It's been true in my experience. Even running games through Wine - for the games that work - they run better than they did in Windows.

---

### Post by talsemgeest on 2009-09-12
> **CatKiller said:**
> It's been true in my experience. Even running games through Wine - for the games that work - they run better than they did in Windows.
Heh, maybe I've just been really unlucky then :)

---

