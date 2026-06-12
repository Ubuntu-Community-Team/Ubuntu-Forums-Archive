---
title: "No -buntu will boot after update"
date: 2012-06-25
forum: General Help
---

### Post by Eli1932 on 2012-06-25
Hey there,

After updating the packages of  either Kubuntu 12.04 or Ubuntu 12.04 I cannot boot any longer. It will either hang up at Plymouth or at some password screen. I though my Kubuntu install was corrupt so I went ahead and nuked the OS, after an update, it stopped booting. I thought, oh well perhaps this Kubuntu release doesn't agree with my machine and downloaded Ubuntu 12.04... the same exact results; after an update I cannot boot, I get stuck at Plymouth, the screen that says Ubuntu and has the little dots, the splash screen, you know what I mean....

Now check this out: I ran Kubuntu 11.04 since the day it dropped and never had this problem. Before that I ran Ubuntu and never had any problems with it. 12.04, -buntu, however, will not boot after an upgrade.

I have researched and researched, I found a number of ppl with this problem but have found no solution. As a matter of fact please see this thread I made over on the Kubuntu forums: [http://www.kubuntuforums.net/showthread.php?59306-The-Singularity-has-Arrived/page2](http://www.kubuntuforums.net/showthread.php?59306-The-Singularity-has-Arrived/page2)

Please note post #14 (and ignore 12), there I give my system specs. They are as follows:

Here are my specs according to Windows 7's run command msinfo32:

Current Date

OS Name    Microsoft Windows 7 Home Premium
Version    6.1.7601 Service Pack 1 Build 7601
Other OS Description     Not Available
OS Manufacturer    Microsoft Corporation
System Name    ELIAS-PC
System Manufacturer    Dell Inc.
System Model    Inspiron N7010
System Type    x64-based PC
Processor    Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz, 2527 Mhz, 1 Core(s), 2 Logical Processor(s)
BIOS Version/Date    Dell Inc. A11, 3/31/2011
SMBIOS Version    2.6
Windows Directory    C:\Windows
System Directory    C:\Windows\system32
Boot Device    \Device\HarddiskVolume1
Locale    United States
Hardware Abstraction Layer    Version = "6.1.7601.17514"
User Name    Elias-PC\Elias
Time Zone    Eastern Daylight Time
Installed Physical Memory (RAM)    8.00 GB
Total Physical Memory    7.80 GB
Available Physical Memory    6.17 GB
Total Virtual Memory    15.6 GB
Available Virtual Memory    13.8 GB
Page File Space    7.80 GB
Page File    C:\pagefile.sys

What is the story with this? I tried the lightdm stuff, everything you see in the thread I linked... I really, really want to have my Linux working and it seems as if there is no hope for this particular problem until some update comes down the pipe.

Please any help you can provide would be greatly appreciated. Bear in mind that Ubuntu 12.04 64 bit suffers the same problem, as my Kubuntu 12.04 64bit. I don't care which one we get working. At this point I would absolutely LOVE to use Unity. :p

I have searched these forums and google extensively, but have come up empty handed.

---

### Post by Eli1932 on 2012-06-25
I don't know about that one. ;-)

---

### Post by Eli1932 on 2012-06-25
Dang... all I got was a keylogger.

/cry

---

### Post by jmfal on 2012-06-25
If you can get to the grub screen try running  memtest

Or you  can run it from the cd

Either your CD's are bad or memory might be failing

---

### Post by Eli1932 on 2012-06-25
I can get to grub, and I have run memtest with no issue. I am using booting from a USB stick. I tired another drive when I installed Ubuntu, but still faced the same issue.

---

### Post by Eli1932 on 2012-06-28
Is there anyone who can help with this? I've been trying to research, but can't find much.

---

### Post by nipunshakya on 2012-06-28
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) might help you out... read thoroughly..
Go with the 2nd option mentioned in the link.

Goodluck

---

### Post by Eli1932 on 2012-06-28
@ WinuxUser You fixed it. YOU FIXED IT!!

/bow
/hug
/highfive

Seriously, you have made my day. The best part is that I used this to fix my Kubuntu (don't hate me) install. 

Thanks a ton.

---

### Post by nipunshakya on 2012-06-28
Glad that your system is up and working...

Good-luck and Happy Linuxing

---

