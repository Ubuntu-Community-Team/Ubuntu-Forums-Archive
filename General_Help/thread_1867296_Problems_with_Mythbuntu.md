---
title: "Problems with Mythbuntu"
date: 2011-10-22
forum: General Help
---

### Post by iubunt3 on 2011-10-22
Forget wateboarding, if they want to torture terrorists in Gitmo, they should just leave a pc and a linux cd rom in a room with terorists. Seriously!

I'm not by far a novice, I've been using linux on a limited basis (ie. mostly running servers in the background for home). The most recent (and I mean in the past 7 years or so, is using mythtv).

So it's time for me to upgrade mythtv that has been working well for me. Natural progression with all things considered. It's only been about 4 years since I installed this current version, so I'm going to check for updates to see if there's any. Ah, you're running an old version of fedora... Sorry! All repositories are out of date, nothing to yum get anymore. Do I want to feel lucky to download a source version of mythtv and hope/pray that there's no dependencies that needs to be updated as well? Yeah right, I know better than that!

** That's about one night of torture **

Keep in mind I'm typing this on XP where the OS is over 10 years old now and I have no troubles loading any new software with new drivers, etc. Finding a new copy of Firefox and plugins still works with XP.

So what should I load this time? I'd say uh, the latest version of Mythdora... and off I go to the mythdora website... but no... it's eol'd. So the next natural progression is to use Mythbuntu.

Mythbuntu, an offspring of the more popular Ubuntu. This is the famous OS build that is loved by a lot of people for it's ease and use. So how could I really go wrong?

So first, I thought I would try to recycle some old pcs to see if they would run on them. Stuff I know would handle XP but a little slower that's all. I'm talking PIIIs here since it's just going to be a backend with not much power needed. Sorry! Mythbuntu will try to install and just crap out. It took me at least 5 retries to then understand it's just not going to work. Ended up working on a newer 1.2ghz Celeron and also needed at least 512mb of ram to even get it going. 256mb caused some issues that I don't quite remember.

** That's about two nights of torture **

And I decided to build a new PC becuase that backend was idling at around 60watts. Way too high for the PII it was replacing at 35 watts. Purchased some AMD Athlon 250 and hardware. So this should be a piece of cake right? AM3 cpu, all recent hardware, DDR2, everything that shouldn't be an issue becuase the hardware is just too old right? Well keep on reading..

So ok, Mythbuntu installed fine with the new hardware. It's got a 8300 built in GPU, so naturally I would select the Nvidia drivers because I do want the VDPAU acceleration. It's something that I was never been able to play was 1080P content. Instalation goes well and it reboots. Ugh, I immediately get a screen that was 640x480. Seriously? Off I go to hunt for what the current linux display widget is (it changes every flavor of linux I install). I finally find the ubuntu display widget, and yes 640x480 and 320x240 was offered. That's fabulous guys... so I find the Nvidia widget and it at least offers me 1024x768. Now I'm a seasoned linux installer so I know what has to be done next is sit through websites after websites sifting through pages of linux and ubuntu forums and documents until I find something similar to some xorg.conf file that I need to custom resoution. Seriously? 10 years ago I'd understand that, but is this how far linux has progressed?

** another night not totally wasted but at least disgusted **

Now this night I decided to tackle the power issue. The new rig is idling at 40 watts. The problem is that the voltage they used is too conservative. I just know that from all the other research I've done that it should be around 30-35watts. So I search on about undervolting the AMD chip. Quick google results in a tool for XP called k10stat. That gives you a nice graphical GUI that gives you the ability to change the p states from P0 to P4 easily.

How about for linux, or more specifically for Ubuntu. Yeah right... I'm getting posts from 2005 about something similar but knowing how Linux is, if it's not recent, you might as well forget about reading about it. So I have to scour over tens of pages...

Finally get to some website that talks about the powernow-k8 module. It should even give you some information about the voltages! This is what the other people had posted:
powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.50.4)
powernow-k8:    0 : fid 0x0 (800MHz), vid 0x12 (1100 mV)
powernow-k8:    1 : fid 0x8 (1600MHz), vid 0xa (1300 mV)
powernow-k8:    2 : fid 0xa (1800MHz), vid 0x6 (1400 mV)
powernow-k8:    3 : fid 0xc (2000MHz), vid 0x2 (1500 mV)

Oh cool! it even lists all the voltages! So let me see what mine says!
[    0.925543] powernow-k8: Found 1 AMD Athlon(tm) II X2 250 Processor (2 cpu cores) (version 2.20.00)
[    0.925581] powernow-k8:    0 : pstate 0 (3000 MHz)
[    0.925582] powernow-k8:    1 : pstate 1 (2300 MHz)
[    0.925584] powernow-k8:    2 : pstate 2 (1800 MHz)
[    0.925585] powernow-k8:    3 : pstate 3 (800 MHz)

Wtf? Why does it only lists the mhz? Great, I knew it couldn't be that easy. Well who cares, I'm getting closer. At least I know the powernow-k8 is loaded in Mythbuntu. So more research into it and I find that you can customize the powernow-k8 module. So is this what is fustrating? Downloading modifying and compiling it? Actually no, it is a piece of cake, remember this is a fresh install of the latest version so apt-get has no problems getting the source, nor did compiling had any issues. So the next thing is to try my brand new compiled version. So I typed modprobe -r powernow-k8 to remove the module...

# modprobe -r powernow-k8
FATAL: Module powernow_k8 is builtin

Wtf? it's built into the kernel? Ubuntu decided to include that in some version 10 or 11 or something like that. The website I was reading was running Ubuntu 9 (remember what I said about reading articles that are a couple years old earlier?) That means I have to do a full kernel recompile??? Hell no... this is way to difficult. Another wasted effort there!

So looking around, I find another glimmer of hope, there's another tool called cpupowerd. Looking at the website, it says the only CPU it supports are K8 types. Great! there's no issues there I hope! Another quick download, and another quick compile, I have a binary.

I run the binary.

# cpupowerd -s
cpupowerd 0.2.1 written by Markus Strobl.
WARNING: This program could cause damage to your Hardware!
MSR-File </dev/cpu/0/msr> doesn't exist, please load the msr kernel module!
Initialisation failed!

Geez, another search on the web, I find there's a module called msr. So a quick modprobe msr fixed that

# cpupowerd -s
cpupowerd 0.2.1 written by Markus Strobl.
WARNING: This program could cause damage to your Hardware!
AMD-Model <0> not supported!
Initialisation failed!

WTF??? I have just spent the whole day reading, downloading, compiling, and failing to get something that I could do in minutes on XP.

So before you say..Why are you using linux? It sounds you have an issue with it.
Yes and no! Ubuntu was supposed to be this great distribution. I still find that it has all the faults of linux since I've been using it for over 15 years. It's only good if you never touch the underbelly of it. Once you do, you're doomed and nothing has changed to improve this. I'm using XP that is over 10 years old and it just works. Is it the fault of the unix? Look at OSX, it's got a unix base, it runs fine. You run the binaries and it just works. Not like linux, you can get binaries/executables as long as the version is supported. So we're talking about 2-3 years tops. Then you will run into issues about dependencies etc. with other modules that makes it obsolete. Besides that, who actually knows how to download and compile a source code? You would have figured that in all these years someone would come up with some standard to make it easier to get precompiled binaries for linux. It's their biggest crux.

Talk about fustration. I dread upgrading mythtv, because it literally means spending at least two to three weekends to get through it. And this time round, nothing has changed. I even left out a whole bunch of other steps that will take me nights to figure out. The lirc remote for example, for some reason the old version detected it fine, but not this version, so I have to get around it another way and that means finding more scripts to load and hope to get all the buttons mapped right, that's another ordeal. I'm not even done yet. But all I know is that for using Linux as long as I have, Linux has not progressed at all.

Ugh.

If someone knows a good way to resolve the undervolting issue would be great! I'm using what looks like the version of Mythbuntu 11.04. I have no idea what version of Ubuntu it is. uname -a says  2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 athlon i386 GNU/Linux

---

### Post by rsvancara on 2011-10-22
I am sorry you are having so many problems.  I have spent many nights toiling over mythbuntu installations.  MythTV/Mythbuntu works great when you are using well supported hardware.  A key success factor is proper hardware selection.  

I have not tried any of the powernow tools.   I will keep watching this thread to see if you can make any progress.

If you are using Mythbuntu 11.04, then you are using Ubuntu 11.04.  

You might want to check on the MythTV forums for recommended hardware.

Randall
[http://www.knowyourlinux.com](http://www.knowyourlinux.com)

---

### Post by iubunt3 on 2011-10-23
Thanks, I'm glad I'm not the only one feeling this. It's not even anything related to hardware of mythtv. I'm talking regular Ubuntu stuff. Stuff if I was just to make a regular Ubuntu desktop that I would have to deal with. 

Undervolting is not supported in Ubuntu. It is even frowned upon it seems. Look at this request for it... [http://brainstorm.ubuntu.com/idea/24567/](http://brainstorm.ubuntu.com/idea/24567/)  
the idiot response summed up was, 'why would you do that??? it's like overclocking, it leads to an unstable system.' Seriously? That's the only reason why anyone wouldn't want to make an open source system as open as possible? Even a closed sourced operating system welcomes such attempts at your own risk.

Besides I'm only caring about undervolting it when it's at the idle state. This is where most PCs stay at most of the time when it's idle. So when the governor ramps down to it's idle p3 state at it's idle 800mhz speed, it's going to consume the least amount of power. When I need it to ramp up to the p0 state at it's full 3200mhz, I really don't care if it consumes more power at this point.

I installed XP dual boot on the system and yes I was able to get it to idle at around 34 watts with the p3 state ramped down to about 0.8v for both the cpu and northbridge voltage without any issues. Dual booting into Mythbuntu yields 40 watts.

---

