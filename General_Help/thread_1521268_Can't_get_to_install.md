---
title: "Can't get to install"
date: 2010-06-30
forum: General Help
---

### Post by clayman1000x on 2010-06-30
I can't make a cd or dvd of the 10.04 LTS to work, I have tried 2 different cd's and a dvd. I have dl from different places but I always get this error when trying to install from cd or dvd media(see attachment). I don't know why this would be doing this as I have already installed this once in dual boot but nuked my system last week. I have XP all setup now but can't get Ubuntu or Kubuntu to install. I am about to try and find 9.10 and see if I can get that to work.

---

### Post by dave_man137 on 2010-06-30
What program did you burn the iso with?

---

### Post by clayman1000x on 2010-06-30
> **dave_man137 said:**
> What program did you burn the iso with?

I have tried infrarecorder, gburner, isobuster, imgburn and alcohol 120%, I don't have Daemon running either if that makes a difference. I also tried the wubi.exe installer under alternative installers, I get the same error. For some reason wubi will not run. I have had no trouble installing games from cd or hdd. I can't find the 9.10 version either at Ubuntu.com

---

### Post by dave_man137 on 2010-06-30
Maybe you could try re-downloading it from ubuntu,I dont think it's the version.
One time I had a problem with a Linux download I burned the thing 5 times and would not install.

---

### Post by clayman1000x on 2010-06-30
> **dave_man137 said:**
> Maybe you could try re-downloading it from ubuntu,I dont think it's the version.
One time I had a problem with a Linux download I burned the thing 5 times and would not install.

I already have tried that, I even tried the torrent file and the 64 bit edition, I lost count how many coasters I threw out. The dl even passed a hash check.

---

### Post by clayman1000x on 2010-06-30
I finally got it to do some sort of install as I did this: I put the last disk I burned back in the drive, shut down the error with System Explorer, then reboot to cd, my bios is set to boot from cd first, I did the install, went through all of the questions it asked, then it kicks out the cd to reboot but won't reboot into anything but windows. 
I looked at my system start up and recovery tabs, settings in XP, and Ubuntu is not even listed, I told the installer to boot alongside windows, 
this is also weird, 

> [boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimerWhat is "/usepmtimer", I have never seen that in a boot loader before. 
Ubuntu seemed to have installed and now I have a new partition in my sata drive where Ubuntu is supposed to be I assume.
Ubuntu does not show up in add remove programs either like it used to.

---

### Post by clayman1000x on 2010-06-30
I now have Ubuntu installed

---

