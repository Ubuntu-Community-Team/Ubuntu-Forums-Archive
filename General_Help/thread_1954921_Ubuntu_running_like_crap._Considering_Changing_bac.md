---
title: "Ubuntu running like crap. Considering Changing back to Windows"
date: 2012-04-08
forum: General Help
---

### Post by DeathByLinux on 2012-04-08
Hey guys,
         I am at my wit's end, here. I have had problems running ubuntu for a while, and haven't really switched back to Windows because it is a pain in the *** to reinstall that system. 
My computer runs very choppy, under Ubuntu. Even typing this, I see that my text shows up considerably later than when I type it on the keyboard. When I look at my system monitor, BOTH of my processors are operating at maximum capacity. This makes my computer run like crap. I don't understand what I am doing wrong here. 
       I have a u400 Toshiba satalite, 2GB of ram and nearly a gig of SWAP. I don't understand why my computer can't handle something as simple as watching a flash video. 
Can you guys tell me what I am doing wrong? This is just getting too ridiculous.

---

### Post by haqking on 2012-04-09
> **DeathByLinux said:**
> Hey guys,
         I am at my wit's end, here. I have had problems running ubuntu for a while, and haven't really switched back to Windows because it is a pain in the *** to reinstall that system. 
My computer runs very choppy, under Ubuntu. Even typing this, I see that my text shows up considerably later than when I type it on the keyboard. When I look at my system monitor, BOTH of my processors are operating at maximum capacity. This makes my computer run like crap. I don't understand what I am doing wrong here. 
       I have a u400 Toshiba satalite, 2GB of ram and nearly a gig of SWAP. I don't understand why my computer can't handle something as simple as watching a flash video. 
Can you guys tell me what I am doing wrong? This is just getting too ridiculous.

use system monitor or

```
top
```

from terminal

to see what process or processes is using the CPU %

---

### Post by DeathByLinux on 2012-04-09
> **haqking said:**
> use system monitor or

```
top
```

from terminal

to see what process or processes is using the CPU %

1. System Monitor near 50%
2. nautilus
3. Chromium

This changes to 
1. When I was watching something on Chromium
I don't see why my 2 1.7 ghz processors can't handle me playing a flash video, which runs like crap, by the way. 

I wrote that I have 2 gigs of ram and nearly a 1 gig of SWAP and 2 1.7 ghz processors. What does Ubuntu need to operate smoothly? 
-DeathByLinux

---

### Post by Yellow Pasque on 2012-04-09
The Flash plugin is terribly inefficient on Linux and has brought many a CPU to its knees.

> System Monitor near 50%
Use htop because sysmonitor is buggy.
```
sudo apt-get install htop
htop
```

---

### Post by DeathByLinux on 2012-04-09
> **Temüjin said:**
> The Flash plugin is terribly inefficient on Linux and has brought many a CPU to its knees.


Use htop because sysmonitor is buggy.
```
sudo apt-get install htop
htop
```

So, what is the solution to getting aound Flash? I mean, Flash is a huge part of the internet, surely there are people running Linux that aren't pulling their hair out like I am. Can you suggest what I can do to make it run more efficiently? Or is this just a downfall of Linux?

-DeathByLinux

---

### Post by Yellow Pasque on 2012-04-09
It's a downfall of Linux, though Flash is slowly dying with advent of HTML5. There's a Firefox plugin called Flashvideoreplacer that works on popular sites.

---

### Post by jadtech on 2012-04-09
other then a few minor issues I dont find I have much trouble with flash and videos in many ways less then running on windows..

---

### Post by DeathByLinux on 2012-04-09
> **jadtech said:**
> other then a few minor issues I dont find I have much trouble with flash and videos in many ways less then running on windows..

Sorry to pry, but could you please tell me your system specs, including video card?

---

### Post by mojorising on 2012-04-09
2GB of RAM should be enough to get by, though your computer won't be fast (it shouldn't be as slow as it appears to be). Flash isn't *that* bad on Linux. It's totally usable and shouldn't grind a machine to a halt. 

I would keep the number of programs you are running to a minimum and see if that helps. Try Firefox instead of Chromium as another test. It would be a good idea to have top running while you're doing this experimenting. 

When running top, you can hold shift and press the "M" key to sort by memory usage. The RES column is the main one to look at to see what's using the most memory. type 'man top' (without the quotes) at the command line for all the details on top. 

You may also want to try a light desktop like XFCE. It's quite nice and uses less memory and CPU than Unity / Gnome does. Another cool light weight desktop is Razor-QT but it's new and I haven't tried it yet. So it's worth checking out but it might not be what you're looking for quite yet. 



Mike

---

### Post by flurospar on 2012-04-09
You might want to use Firefox + Noscript (scripts allowed but all plugins blocked). That way, you can still click on the flash applet when necessary, but otherwise the applets wont be running and wont bring your computer on your knees.

---

### Post by Yellow Pasque on 2012-04-09
> **mojorising said:**
> 2GB of RAM should be enough to get by, though your computer won't be fast.

Having "only" 2GB of RAM is not going to slow a system down unless the user is doing something very RAM-intensive (e.g. 500 browser tabs and running a VM).

> Flash isn't *that* bad on Linux. It's totally usable and shouldn't grind a machine to a halt.
Ever tried 1080P video in the Flash plugin?

---

### Post by Vaphell on 2012-04-09
> 1. System Monitor near 50%
2. nautilus
3. Chromium

system monitor is very cpu heavy for some reason so it skews results a lot. Kill it before running top/htop
besides what gfx card you have and which drivers are installed

---

### Post by kimda on 2012-04-09
I have a small laptop here with also 2 GB of memory and it can even run 720p movies fine (acer 1810t) only with the 1080p movies it will get choppy which it would also with Windows because of the videocard.

[https://friendly.ubuntu.com/11.10/TOSHIBA/Satellite%20U400/I:KBnYp:Cn2:I8g:RAM:BKJ/](https://friendly.ubuntu.com/11.10/TOSHIBA/Satellite%20U400/I:KBnYp:Cn2:I8g:RAM:BKJ/)

Have you tried running another kernel?

---

### Post by DeathByLinux on 2012-04-09
> **mojorising said:**
> 2GB of RAM should be enough to get by, though your computer won't be fast (it shouldn't be as slow as it appears to be). Flash isn't *that* bad on Linux. It's totally usable and shouldn't grind a machine to a halt. 

I would keep the number of programs you are running to a minimum and see if that helps. Try Firefox instead of Chromium as another test. It would be a good idea to have top running while you're doing this experimenting. 

When running top, you can hold shift and press the "M" key to sort by memory usage. The RES column is the main one to look at to see what's using the most memory. type 'man top' (without the quotes) at the command line for all the details on top. 

You may also want to try a light desktop like XFCE. It's quite nice and uses less memory and CPU than Unity / Gnome does. Another cool light weight desktop is Razor-QT but it's new and I haven't tried it yet. So it's worth checking out but it might not be what you're looking for quite yet. 



Mike

How do I change my desktop? I hate Unity, actually. I have been meaning to do something about it.
-DeathbyLinux

---

### Post by Eirreann on 2012-04-09
> **DeathByLinux said:**
> How do I change my desktop? I hate Unity, actually. I have been meaning to do something about it.
-DeathbyLinux

I think we're stuck with Unity for now... 12.04 won't use Unity, I hope...

Anyway, mate, it is strange that you are having such a bad experience with Ubuntu; I'm running at pretty terrible specs as yours, and am only experiencing some lag when dragging windows around on my desktop...
Just out of curiosity, did you install Ubuntu via the Windows Installer or via a disc?  That probably won't mean anything, but I'm just curious.

---

### Post by PhantomTurtle on 2012-04-09
> **DeathByLinux said:**
> How do I change my desktop? I hate Unity, actually. I have been meaning to do something about it.
-DeathbyLinux

To install xubuntu, open terminal and run the following,
```
sudo apt-get install xubuntu-desktop
```
Select xubuntu at the login screen

To install lubuntu, open terminal and run
```
sudo apt-get install lubuntu-desktop
```
Select lubuntu at the login screen

---

### Post by DeathByLinux on 2012-04-11
> **PhantomTurtle said:**
> To install xubuntu, open terminal and run the following,
```
sudo apt-get install xubuntu-desktop
```
Select xubuntu at the login screen

To install lubuntu, open terminal and run
```
sudo apt-get install lubuntu-desktop
```
Select lubuntu at the login screen

**Is it hard to switch back from this? From what I understand, Xubuntu is an entirely different operating system that is built upon Ubuntu. I am seriously considering this. I have hated Unity and want a light and simple desktop. **
Then, regarding Flash, I want to see if I can strip down firefox to the point where it eats very little CPU capacity and I think that should do the trick,because as of right now, flash is less of a hog on Firefox than it is on Chromium.
-DeathbyLinux

---

### Post by PhantomTurtle on 2012-04-11
> **DeathByLinux said:**
> **Is it hard to switch back from this? From what I understand, Xubuntu is an entirely different operating system that is built upon Ubuntu. I am seriously considering this. I have hated Unity and want a light and simple desktop. **
Then, regarding Flash, I want to see if I can strip down firefox to the point where it eats very little CPU capacity and I think that should do the trick,because as of right now, flash is less of a hog on Firefox than it is on Chromium.
-DeathbyLinux

No it isn't you can go back to unity anytime you want by selecting it from your login screen. Also Xubuntu is a Desktop Environment called XFCE like GNOME and KDE. It is not a separate operating system. Additionally it can easily be removed by removing the packages installed by Xubuntu.

---

### Post by Eirreann on 2012-04-11
> **DeathByLinux said:**
> **Is it hard to switch back from this? From what I understand, Xubuntu is an entirely different operating system that is built upon Ubuntu. I am seriously considering this. I have hated Unity and want a light and simple desktop. **
Then, regarding Flash, I want to see if I can strip down firefox to the point where it eats very little CPU capacity and I think that should do the trick,because as of right now, flash is less of a hog on Firefox than it is on Chromium.
-DeathbyLinux
The way it works is that you can select either Ubuntu or Xubuntu at the login screen (the gear icon next to your name) and you'll boot into that.  You can uninstall Xubuntu (if you ever need to) with the code here:
[http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)

I think that you'll like Xubuntu! It's much faster than Ubuntu if you have an older PC and has a nice, simple layout but still retains all of the favoured modern PC functions!

---

### Post by jadtech on 2012-04-11
> **DeathByLinux said:**
> Sorry to pry, but could you please tell me your system specs, including video card?

sorry I missed this 

running Ubuntu 11.10 64bit

dell Inspiron M5030
AMD athlon P360 dual core 2.3 GHZ
memory 2.7Gib
video card ATI/AMD grapics

using both chrome and firefox 

this particular install of Ubuntu was using wubi and is about 3 days running strong no issues ..

---

