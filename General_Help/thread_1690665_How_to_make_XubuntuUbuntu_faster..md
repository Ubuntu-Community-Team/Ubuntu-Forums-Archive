---
title: "How to make Xubuntu/Ubuntu faster."
date: 2011-02-18
forum: General Help
---

### Post by MourningsEnd on 2011-02-18
I have 1 GB RAM, 2.2 Ghz P4, GeForce 8400 GS.

I have Xbunutu 10.10.

Is there anyway I can make it faster?  Particularly with YouTube/Flash/Network/Graphics...lol how can I just make it faster?

---

### Post by MourningsEnd on 2011-02-18
Please, can anyone help me?

---

### Post by TeoBigusGeekus on 2011-02-18
One word: openbox.

---

### Post by Zomby Woof on 2011-02-18
My 2 gHz P4 was okay using Ubuntu 10.04 once I took the ram to 1.5G and upgraded to an ATI 9550. But I did NOT enable any vidual effects. Had no problem with Youtube stuff.

---

### Post by MourningsEnd on 2011-02-18
I don't know that is, please elaborate.

---

### Post by kerry_s on 2011-02-18
:lolflag: you can get a better more powerful machine. :lolflag:


just use lighter apps, somethings you can't help, such as flash & network. flash your at the mercy of adobe, network depends on how much your paying for, pay your isp for faster speeds.

---

### Post by TeoBigusGeekus on 2011-02-18
Switch your window manager; use openbox or, simply, lxde (lubuntu).

---

### Post by MourningsEnd on 2011-02-18
I have fastest speeds possible from my ISP.

Also, I still don't quite get what you're talking about.

Just tell me where I can get it; terminal command.

---

### Post by TeoBigusGeekus on 2011-02-18
> **MourningsEnd said:**
> Just tell me where I can get it; terminal command.
It's not as simple as that; I'm talking about a reinstallation here.
Instead of xubuntu, install lubuntu.

I use a P4 at 3gh, with 1 Gb of ram and a Nvidia Geforce 6600gt with Arch linux and standalone openbox: everything is snappy and speedy.

---

### Post by MourningsEnd on 2011-02-18
I'm not doing an Installation of a new OS.

What else can I do besides that.

---

### Post by Bitrate on 2011-02-18
Upgrade you RAM to 2GB.

---

### Post by MourningsEnd on 2011-02-18
1 GB is my max I believe, the computer is 7 years old.

Don't suggest a new computer or any hardware upgrades.

What's something I can do software-wise to make it faster?

---

### Post by arvevans on 2011-02-18
By slow speed I am assuming you mean that the computer is slow, not that your network is slow.

There are several on-line speed-test web sites that can run tests to tell you what throughput speeds you are getting on your network access.  


You can use the "top" command to see what is taking up most of your CPU cycles.  Once you know which function is hogging system resources you can make some educated guesses for decreasing that load on your CPU.  

In my system it is normal for firefox and chrome to be using up to 20% of memory and xorg to be using between 1 and 20% of cpu cycles.  Everything else is 1% or less unless I am exercising a particular application.

Swap file size should be at least as large as your RAM to facilitate the offloading of sleeping applications if you are running short of RAM space.
Try to not leave large applications open on other desktops when you really don't need them readily available.

---

### Post by williamts99 on 2011-02-18
> **MourningsEnd said:**
> I have fastest speeds possible from my ISP.

Also, I still don't quite get what you're talking about.

Just tell me where I can get it; terminal command.


From the command line
```
sudo apt-get install lubuntu-desktop
```

When that is finished installing, reboot :)

---

### Post by mr_luksom on 2011-02-18
Duplicate post

---

### Post by mr_luksom on 2011-02-18
Either op is a hard marker on speed, or there is something wrong with his setup. I have an almost identical machine (no gfx card), and full ubuntu, let alone xubuntu is very speedy. I used to use lubuntu on my 256mb 1.7GHz Celeron laptop because I found xubuntu a little slow.

OP, can you post the output of:
```

top
xrandr
free
hdparm -tT "main partition"

```

Where "main partition" is the partition ubuntu is installed on, like /dev/sda1 or /dev/hda1

---

### Post by Bigtime_Scrub on 2011-02-18
Xubuntu is your best bet to speed things up. Xfce is more lightweight than Gnome. 1 gig is more than enough. The choice of applications you use and have on your system is important. 

I would look at what something like CrunchBang has installed by default and use those programs and get rid of the programs that would then be duplicates.

For example install Google Chrome as your web browser and get rid of Firefox. use VLC, xfburn, pidgin. For a quicker bott up into your desktop look at the programs that are run at start up and unselect things you do not need like blue tooth or printer support (cups) or anything else you know for sure you dont need. 

To be honest though Xubuntu has gotten very bloated, it is no faster than plain old Ubuntu with Gnome which is ridiculous. I used to love it.

---

### Post by MourningsEnd on 2011-02-18
My problem isn't like, slow boot-up..or programs and whatnot.

It's my Flash video, like on YouTube..or other sites I won't mention.  The video lags..and I don't like it.  When I have a Flash video going, it's like...70% of my CPU; which is normal.

---

### Post by cottfcfan on 2011-02-19
Your not alone with that problem, I have 3 gig ram and have the same issue.
Unfortunately this is a Linux/Flash problem, and has been for a long time.
The only thing I can suggest is try turning off all your visual effects when watching a Flash vid, and make sure you have the latest flash installed, there is a Firefox addon called "flash-aid" that may help.

---

### Post by Spyderkid on 2011-02-19
set all your graphical settings to lower don't enable as many effects use light versions of programs

---

### Post by MourningsEnd on 2011-02-19
I use Chormium, yanno Linux version of Google Chrome.

It comes with Flash.

Also, how can I switch my settings to low?

---

