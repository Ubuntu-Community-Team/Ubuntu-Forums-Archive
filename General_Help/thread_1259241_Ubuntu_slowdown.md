---
title: "Ubuntu slowdown"
date: 2009-09-06
forum: General Help
---

### Post by dmillerw on 2009-09-06
I am currently running Ubuntu 9.04, and while of some of it is fast, other bits are much slower then windows, which is not what I expected

SPECS-

Intel Pentium 4 2.00GHz
1280MB of RAM
NVIDIA 6200 256MB VRAM using NVIDIA driver 180.44

PROBLEMS-

While listining to music using Rythmbox, the music will skip randomly, mostly while using firefox.

Firefox seems quite laggy, especially while viewing Flash movies/games

and for some reason, my middle mouse button doesn't work...

--

Any ideas at all?

This is bugging me, and is what has caused me to switch back to Windows before

---

### Post by DeMus on 2009-09-06
> **dmillerw said:**
> I am currently running Ubuntu 9.04, and while of some of it is fast, other bits are much slower then windows, which is not what I expected

SPECS-

Intel Pentium 4 2.00GHz
1280MB of RAM
NVIDIA 6200 256MB VRAM using NVIDIA driver 180.44

PROBLEMS-

While listining to music using Rythmbox, the music will skip randomly, mostly while using firefox.

Firefox seems quite laggy, especially while viewing Flash movies/games

and for some reason, my middle mouse button doesn't work...

--

Any ideas at all?

This is bugging me, and is what has caused me to switch back to Windows before


Well, your hardware is more than capable of running Ubuntu, especially the 1280MB Ram.
Concerning your nVidia driver: how did you install it? Through Synaptic or did you download the driver from the nVidia site?
What does "Hardware drivers" tell you? (System --> Administration --> Hardware drivers)?
When things are as slow as you say it is probably a wrong driver which makes the CPU do extra work which is normally done by the GPU.

---

### Post by dmillerw on 2009-09-06
This is all the Hardware Drivers window shows
[[img]http://img143.imageshack.us/img143/8757/screenshot009v.th.png[/img]](http://img143.imageshack.us/img143/8757/screenshot009v.png)

I installed the driver using EnvyNG

---

### Post by DeMus on 2009-09-06
> **dmillerw said:**
> This is all the Hardware Drivers window shows
[[img]http://img143.imageshack.us/img143/8757/screenshot009v.th.png[/img]](http://img143.imageshack.us/img143/8757/screenshot009v.png)

I installed the driver using EnvyNG

Okay, so you have the best driver for your hardware. So far so good.
Now open a terminal (Applications --> Accessories --> Terminal) and type top
You will see a list of programs which are currently running. In the column CPU you can see how much CPU power a program uses, the one which uses most is on the top of the list.
You can make a screendump and paste it here, or simply write the names of the program(s) which eat(s) a lot of CPU power.
To stop "top" simply press q (quit) and close the terminal window if you want.

---

### Post by scouser73 on 2009-09-06
> **dmillerw said:**
> I am currently running Ubuntu 9.04, and while of some of it is fast, other bits are much slower then windows, which is not what I expected

SPECS-

Intel Pentium 4 2.00GHz
1280MB of RAM
NVIDIA 6200 256MB VRAM using NVIDIA driver 180.44

PROBLEMS-

While listining to music using Rythmbox, the music will skip randomly, mostly while using firefox.

Firefox seems quite laggy, especially while viewing Flash movies/games

and for some reason, my middle mouse button doesn't work...

--

Any ideas at all?

This is bugging me, and is what has caused me to switch back to Windows before

A quote from a previous post by DeMus: 
> If you want to use it in Firefox do this:
Menu Edit | Preferences
Tab Advanced, sub tab General
Make sure "Use autoscrolling" is On. If you like you canalso switch on: "Use smooth scrolling" but I did not see any difference here.

---

### Post by dmillerw on 2009-09-06
[[img]http://img193.imageshack.us/img193/4206/screenshot010t.th.png[/img]](http://img193.imageshack.us/img193/4206/screenshot010t.png)

---

### Post by dmillerw on 2009-09-06
Its not only firefox, the middle mouse button doesn't work anywhere.

---

### Post by DeMus on 2009-09-06
> **dmillerw said:**
> [[img]http://img193.imageshack.us/img193/4206/screenshot010t.th.png[/img]](http://img193.imageshack.us/img193/4206/screenshot010t.png)

Your Xorg value is pretty high, compared to mine where it is between 2 and 4 %. This would indicate something being not correct in the graphical department after all.
Swiftfox is also extremely high but that could be a peak value. Do you always have a lot of programs open at the same time? hen you don't do that, is each program running fine then? I mean, one program at the time.

---

### Post by dmillerw on 2009-09-06
Each program works fine on its own, and I do usually multi-task

Would the xorg.conf help by any chance? help figure out the high Xorg CPU value?

---

### Post by DeMus on 2009-09-06
> **dmillerw said:**
> Each program works fine on its own, and I do usually multi-task

Would the xorg.conf help by any chance? help figure out the high Xorg CPU value?

Somebody else can help here please? Any ideas why this PC is slow?

---

### Post by Cardale on 2009-09-06
Ubuntu is always buggy with sound for me.  Often times it will totally become disabled in my browser.  I had a lot of problems with Flash videos on you tube as well.

One thing that help was I used flash instead of open source alternative.

---

### Post by dmillerw on 2009-09-06
I'm using Flash as well

---

### Post by dmillerw on 2009-09-06
Well, I'm going to bed, maybe when I wake up there will be some more posts...

---

### Post by lovinglinux on 2009-09-06
For Firefox performance see [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by dmillerw on 2009-09-06
I went through that, helped a bit, things still lag though.

---

### Post by lovinglinux on 2009-09-06
> **dmillerw said:**
> I went through that, helped a bit, things still lag though.

Yep. It just helps, because flash is problematic in Linux.

---

### Post by dmillerw on 2009-09-06
Figures, oh well

Any ideas on why Xorg has such a high CPU usage?

---

### Post by lovinglinux on 2009-09-06
> **dmillerw said:**
> Figures, oh well

Actually, I mixed things in my reply, since you were not talking about flash. I guess there are too many flash threads that my replies are becoming automatic :)

> **dmillerw said:**
> Any ideas on why Xorg has such a high CPU usage?

Probably graphics card driver. How much CPU does it use and in which conditions?

---

### Post by alejaaandro on 2009-09-06
from my experience flash has always been a huge problem in linux thanks to adobe that does a shitty job for linux.. i THINK i remember reading somewhere that flash video isn't directed to nvidia cards (or maybe even any graphics cards, don't really remember), so cpu has to do all the work..
my only workaround all these years is using flashblock (add-on) which replaces each flash component with a button.. if you want to see it, just click on it and it starts.. that way i only see what i want and stupid flash adds don't hog my cpu.. cons: sometimes there can be a useful flash menu or something that i overlook thinking it's gonna be an add and i don't click it.. (maybe it should be replaced by a thumbnail, don't know if it's possible.. that's for another forum though)

---

### Post by dmillerw on 2009-09-06
Xorg uses %20-%30

---

### Post by mike555 on 2009-09-06
If you can't get good quality full screen videos , like on hulu.com , you might install " epiphany -webkit " , it doesn't use mozilla , so it works better on videos ..





opp's it doesn't work on Jaunty ... but works great on Karmic.... sorry

---

### Post by lovinglinux on 2009-09-06
> **dmillerw said:**
> Xorg uses %20-%30

In which conditions? Playing videos, viewing a web site with heavy java script or on idle? 

On idle, I get as low as 1%, but usually stays around 3%. When Playing html5 video with javascript controls like [this]("http://www.mozilla.com/en-US/firefox/video/?video=fastest-sport-stacker"), it stays around 25% with a couple of 35-40% spikes.

> **mike555 said:**
> If you can't get good quality full screen videos , like on hulu.com , you might install " epiphany -webkit " , it doesn't use mozilla , so it works better on videos ..

Opera and Chromium uses different engines and they are as bad as Firefox. So I don't believe is Firefox fault, except when some javascript is also involved, which is the case mentioned above.

---

### Post by dmillerw on 2009-09-07
sorry

Idle is %20-%30, watching flash videos is about %40, and watching the video you linked to was %50-%58

---

### Post by photoscotty on 2009-09-07
Vostro 1000/AthlonX2 1.8Ghz/4GB Ram - Ubuntu Studio Jaunty

My idle CPU usage is reporting 50-55%, but when I use top, no processes are using any more than 2%...

At first I figured my system monitor was reporting incorrectly, but I'm experiencing the same slowdown issues as listed above (songs skipping, lockups when multi-tasking)...

Anyone have any ideas what's going on here?

---

### Post by lovinglinux on 2009-09-07
> **photoscotty said:**
> Vostro 1000/AthlonX2 1.8Ghz/4GB Ram - Ubuntu Studio Jaunty

My idle CPU usage is reporting 50-55%, but when I use top, no processes are using any more than 2%...

At first I figured my system monitor was reporting incorrectly, but I'm experiencing the same slowdown issues as listed above (songs skipping, lockups when multi-tasking)...

Anyone have any ideas what's going on here?

We are talking about xorg CPU usage, not overall. But it is still high in your case, which is probably due to vino-server. Got to "System >> Preferences >> Startup Applications" and disable the "Remote Desktop" then reboot. It should reduce your CPU usage considerably.

---

### Post by dmillerw on 2009-09-07
Any ideas?

---

### Post by Cato2 on 2009-09-07
A few things to try to understand what the slowdown is:

1. Install 3 System Monitor applets (right click on Ubuntu's top panel, then Add to Panel option, then choose System Monitor).

2. For System instances 2 and 3, right click on their panel icon and choose Preferences - choose monitoring of Memory and Load (only) for these instances.

3. sudo apt-get install htop, and run htop in a terminal window.

Look out not just for CPU but high 'load average' in htop and system monitor - if you are having a lot of disk I/O then that will show up as load average (no. of processes ready to run at each instant) even if CPU is not high.

Also, type 'free -m' or look at htop's memory and swap data. If you are using any swap at all, that may slow things down a lot.

---

### Post by dmillerw on 2009-09-07
I'm seeming to get CPU major CPU spikes from doing pretty much everything, Load stayed low though

I ran "free -m" said it was using 5 of 4880 swap

---

### Post by photoscotty on 2009-09-07
> **lovinglinux said:**
> We are talking about xorg CPU usage, not overall. But it is still high in your case, which is probably due to vino-server. Got to "System >> Preferences >> Startup Applications" and disable the "Remote Desktop" then reboot. It should reduce your CPU usage considerably.

Tried that suggestion already from another thread. Haven't seen any change yet.

---

### Post by lovinglinux on 2009-09-07
> **photoscotty said:**
> Tried that suggestion already from another thread. Haven't seen any change yet.

Try some of the tips included at [http://ubuntuforums.org/showthread.php?t=1152095](http://ubuntuforums.org/showthread.php?t=1152095)

---

### Post by ankspo71 on 2009-09-07
As for the Flash part of your firefox problem. Flash is a resource hog in any browser and seems to be worse in Linux. I have big trouble with it too on my Intel Celeron 2.2. Some flash games barely work (esp. farmtown at facebook) and videos on youtube barely play. Since you have a Pentium, you might have some luck with enabling hyperthreading to give you a little performance boost. As I understand it though, there is a security risk by doing that.

Flash system requirements:
[http://www.adobe.com/products/flashplayer/systemreqs/](http://www.adobe.com/products/flashplayer/systemreqs/)

Enabling Hyperthreading:
[http://ubuntuforums.org/showthread.php?p=895077](http://ubuntuforums.org/showthread.php?p=895077)
(this doesn't work for me because I use a Celeron processor).
That is an old post, so I don't know if it will be the exact same procedure in later Ubuntu's or do I know if it is already enabled in current Ubuntu's.

---

### Post by lovinglinux on 2009-09-07
> **ankspo71 said:**
> Enabling Hyperthreading:
[http://ubuntuforums.org/showthread.php?p=895077](http://ubuntuforums.org/showthread.php?p=895077)
(this doesn't work for me because I use a Celeron processor).
That is an old post, so I don't know if it will be the exact same procedure in later Ubuntu's or do I know if it is already enabled in current Ubuntu's.

That information about Hyperthreading is outdated. It comes enable by default now and the vulnerability has been addressed. So all you have to do is enable it in the BIOS.

---

### Post by dmillerw on 2009-09-07
> **lovinglinux said:**
> That information about Hyperthreading is outdated. It comes enable by default now and the vulnerability has been addressed. So all you have to do is enable it in the BIOS.
I don't believe my processor has support for Hyperthreading

---

