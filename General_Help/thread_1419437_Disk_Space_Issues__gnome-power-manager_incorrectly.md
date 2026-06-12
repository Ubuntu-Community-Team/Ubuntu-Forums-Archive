---
title: "Disk Space Issues / gnome-power-manager incorrectly configured"
date: 2010-03-01
forum: General Help
---

### Post by gdea73 on 2010-03-01
Well, I'm new to these forums in case you haven't noticed - and I'm new to Ubuntu as well, so excuse any stupid mistakes/questions I may ask. I have only had Ubuntu for 4 days.

Here's the system specs, first of all:
Dell Dimension C521 Desktop
1GB RAM
AMD Athlon 64 2.0 GHz Processor
nVidia GeForce 6150 LE
Came with Windows XP MCE 2005
160GB HDD (3 Partitions: 
1) Storage - 100GB 
2) Windows XP [has been freshly installed since I got the PC] - 15GB or so
3) Ubuntu Linux 9.10 (Karmic) - 23GB *here's my problem*

Well, over the past few days I've already had to reinstall Ubuntu two or three times after "running out of disk space" first and then getting something screwed up at login (common error: gnome-power-configurator *or something* incorrectly configured. Please contact your administrator) where I can only log-in to Failsafe GNOME and I get disk space warning issues. Even after this power thing issue is "fixed" there are display problems, or so I've heard, and so I've had to reinstall every time this occurs.

The thing is, Ubuntu tells me in my Home folder that I have currently 2.3GB of space free. How could that be? If I open the "Disk Usage Analyzer" (which is cool, by the way, but confusing) it shows me I have about 18GB of free space, and interestingly that I have 40GB of capacity. According to Windows XP (and me), Ubuntu seems to be reading the amount of space in my partition wrong and when it thinks it runs out of space it shoots itself, so to speak.

I installed Ubuntu using the "wubi.exe" file that I got from Ubuntu's website, which was convenient as far as I didn't have to set permissions etc. on the partitions - it did it all for me. I realized that my free space before was limited when I selected only 5GB for my "Installation Size", so this time I chose 23GB, the maximum capacity of this partition - but still how could I only have 2GB left? Here's what I've installed:

- EnvyNG for graphics card help
- Splash Screen manager
- FlightGear flight simulator
- WINE, and I'll round off my WINE programs to 500MB
- Just a few small programs I can't seem to remember
- No themes currently

Sorry for such a long message, but I hope you all get the chance to read it and help me. Thanks in advance,

- gdea73

---

### Post by gdea73 on 2010-03-02
So, can anyone please help with this? I don't want to have to reinstall Ubuntu again - or just ditch it altogether.

---

### Post by gdea73 on 2012-03-02
If anyone else runs into this problem, it was because I was running Ubuntu on a FAT32 partition... that didn't work too well. I don't recommend using WUBI for a permanent installation.

---

