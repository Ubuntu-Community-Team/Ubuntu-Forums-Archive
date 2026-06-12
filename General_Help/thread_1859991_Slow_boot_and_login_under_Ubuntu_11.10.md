---
title: "Slow boot and login under Ubuntu 11.10"
date: 2011-10-14
forum: General Help
---

### Post by chilloutmo on 2011-10-14
Hello everyone,

I know this is a busy time as after every upgrade, the forum is flooded with requests, but I would still really appreciate it if someone could answer me. After having upgraded to 11.10, I have experienced quite a substantial performance loss on all fronts. Booting takes about 1min30 and what is especially weird, login takes another 1min30 (!!!). Inside Ubuntu (whether with Unity 3D or 2D doesn't matter), everything also feels a bit slower. Under 11.04 I have not had these issues and boot and login times were "normal". I can only confirm what this article demonstrates: 

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1110_bootchart&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1110_bootchart&num=1)

but I really thought it wouldn't be that bad. Any ideas for help please?

I am running a Asus 1215n Intel® Atom™ CPU D525 @ 1.80GHz × 4 with 2GB RAM and switchable Nvidia ION/Intel graphics.

Thank you very much!

---

### Post by FreudianSlip on 2011-10-14
Hi,
You're not alone.  I've just done the upgrade from 11.04 (which was working fairly well, just the odd hiccup that I was hoping 11.10 would fix) and find that on login it takes about a full minute compared to about 15 seconds previously.  The hard disk light is on constantly during this process.

In addition to this, loading apps like the software centre seem to kick the cr*p out of my hard disk and take forever to load up, and the keyboard repeat seems to have disabled itself, which is a PITA when you realize that you're touch typing 1 char to the right... damn.

I'm running a quad core alienware laptop with 8gb of ram and a 750gb 7200 spin, 32mb cache (or is it 16..cant remember..) drive.


Freudy

---

### Post by someitalian123 on 2011-10-14
I noticed it too, it take about twice as long to load firefox now. Also for some reason when ever I start my pc the audio is always muted.

---

### Post by skder on 2011-10-14
Hi guys, I have the same kind of problem too. 

Boot time = no problem, in comparaison to Natty :)

Shutdown time = 20 seconds, although 5 seconds in Ubuntu 11.04.

I still give a chance to 11.10, but I don't think I'll resist. :(

---

### Post by chilloutmo on 2011-10-14
OK, great so I am not alone, although there seem to be variations of the problem. @Freudy's issue is most similar to mine, and I must say other software has been pretty slow as well (USC, Firefox, etc.). This is my third distro upgrade since 10.04, so I am thinking about a fresh install in the hope of solving the problem, but I really hope somebody in the forum has another idea how to fix this.

---

### Post by mixmastamyk on 2011-10-14
Try booting the Live CD into ram to see if the problem is related to upgrading, or bad video driver, etc.

---

### Post by meadhikari on 2011-10-15
Exact same problem here.
When the system shutdowns, its slow there too.

---

### Post by dralaroc on 2011-10-15
Same here, getting a "waiting for network config" message.  Then "waiting up to 60 more seconds for network confi" message. Seems odd to me.

---

### Post by Call Me Ishmael on 2011-10-16
Me too. HP Pavilion DV6000, after the upgrade to Ubuntu 11.10 the boot time is about five times more. There is any official bug open on Launchpad? It's an ugly regression.

---

### Post by jammaj on 2011-10-16
I am having the same problem. I get a purple background for ages and ages until finally the login screen comes into view. 11.04 was much quicker.

It is annoying, because it is suggested that 11.10 can boot up in 12 seconds:

[http://insanetek.com/news/1-web-and-industry-news/733-ubuntu-1110-oneiric-ocelot-boot-time](http://insanetek.com/news/1-web-and-industry-news/733-ubuntu-1110-oneiric-ocelot-boot-time)

---

### Post by mips on 2011-10-16
Guys, have a look at e4rat.

[http://e4rat.sourceforge.net/](http://e4rat.sourceforge.net/)
[https://wiki.archlinux.org/index.php/E4rat](https://wiki.archlinux.org/index.php/E4rat)

I'll try it out in ubuntu a bit later. I works great in arch & debian where i've used it before.

---

### Post by pdecarlos on 2011-10-16
Same problem here. After upgrade from 11.04 to 11.10, I have only wallpaper for a minute on login and wallpaper and desktop icons 30sec on shutdown.

---

### Post by Lyn0317 on 2011-10-17
same here. I wonder if a fresh install will solve this problem.

---

### Post by Call Me Ishmael on 2011-10-17
Me too. HP DV6000, 2GB Ram + Nvidia GeForce with proprietary drivers.
From dmesg it seems to be a Udev issue, everytime there's a udevd message line, I can see at least 20secs between to consecutive messages.
Probably a new bug shall be filed on Launchpad, it's a serious regression, in my opinion.

---

### Post by avrono on 2011-10-17
Hi All, 

I am having a similar problem - when I upgraded my Wireless network connections were not behaving, I had to delete all unused network connections. Then upon reboot I got and still get a message saying "configuring network connections" and then "waiting 60 seconds .... " . It is taking at least 10 X longer to boot than 11.04

Aside from that applications seem to be running ok, aside from all the broken dependencies in Eclipse etc.

_av

---

### Post by The_Autonomist on 2011-10-22
These exact same problems are happening with me too. I have a HP dv6000 and my computer takes forever to logon. after i type in my password, it just shows my wallpaper for a while (about 1:30 like everyone else said). my volume is also always muted. 

extremely frustrating. i miss the speed of 11.04...:(

---

### Post by mjbennison on 2011-11-02
For me the boot time is not much different to 11.04, however I also suffer from around 30 seconds of wallpaper only - around 10s of the Ubuntu purple and then around 20s of my wallpaper. Then all comes to life. I see nothing obvious in dmesg to help. Many years ago I used bootvis to fix slow startup on Intrepid, but I don't think that there's an equivalent visualiser for post boot (please correct me!). FWIW I'm running the 64bit version of 11.10 (on a home built Q6600, GT430, 8Gbyte RAM).

Like another poster, after update to 11.10 my wireless lan was also troublesome - it never auto connected and I had to do it manually (used to get messages like connecting to 'none' rather than connecting to 'router'). This has 'gone away' - I am assuming one of the many updatres since has corrected the problem.

---

### Post by inspiral on 2011-11-03
I've got broadly the same issues, on my Asus Atom Nvidia Ion based system.

It sit for ages on a blank purpley screen before the mouse pointer appears then it's another age before Unity comes up. The system used to take just 45 seconds including POST.

I updated to 11.10 from 11.05, the latter being a clean install.

Cheers

---

### Post by Lamukra on 2011-12-08
Probably have some solution for you here guys. At least worked for me

I am using open Source Driver Radeon with ATI Xpress 1250

1. Check Your Bios for any kind of LegacySupport and disable it

2. Go to CompizConfig SettingManager disable PNG Image Loading and GrabHandler plugins and Bailer plugin. GrabHandler Should be disabled first because otherwise you won't be able to disable PNG

this should improve a bit of the loading time

Want to fix purple screen

```
1. Ctrl+Alt+T
2. sudo su
3. echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash
4. update-initramfs -u
5. gedit /etc/default/grub
6. Uncomment line with GFX_MODE=640x480

Something like this

7. update-grub
8. update-initramfs -u - just incase
9  exit
10. Reboot your Machine
```

It Helped Me

---

### Post by mjbennison on 2011-12-11
> **Lamukra said:**
> 
1. Check Your Bios for any kind of LegacySupport and disable it

2. Go to CompizConfig SettingManager disable PNG Image Loading and GrabHandler plugins and Bailer plugin. GrabHandler Should be disabled first because otherwise you won't be able to disable PNG

this should improve a bit of the loading time


I tried these two suggestions but neither made any difference, thanks for the suggestions anyway!

As for e4rat mentioned earlier, it seems to only be for boot time improvement, which isn't really my problem. It's the usable desktop which I have to wait 30 or so seconds. I assume that this is a timeout for something but I don't have a clue where to start looking.

---

### Post by jammaj on 2011-12-20
The news from my end is that it the speed of boot up has greatly improved. I didn't change anything - I just assume that some of the system updates that I have downloaded since the initial upgrade have had a positive effect. It is now about as fast as before - like 20 seconds boot up time in total.

---

### Post by mjbennison on 2011-12-20
I am glad that you have had a positive result. For me it is still the same, depite all the recent system updates :(

---

