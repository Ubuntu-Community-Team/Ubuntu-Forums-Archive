---
title: "I really messed up my computer"
date: 2009-11-07
forum: General Help
---

### Post by peikojose on 2009-11-07
First sorry for my english-
Hi, today I was trying to install Windows 7 and the new Ubuntu 9.10 in my Asus EEE 900HA.
I installed Windows 7 without a problem (Overwriting the XP that came with the 900HA), it was running very good. So I downloaded Ubuntu 9.10 "Netbook Remix" to install and test it... 
I think I installed it ok! But I really didn't like it (I prefer the desktop version). 
So, I did think about reinstall everything again but this time with the desktop version of ubuntu...
When I tried to do that I noticed that F9 was not working to restore the system (As this computers don't have a DVD unit, pressing F9 "resets" the computer to its factory settings).... Then I wait for the boot loader of linux to load (Grub) and it had like 6 options I think:
Ubuntu 9.10
Windows 7
Windows XP
Memory Test
So I said, maybe the "Windows XP" selection would take me to the restoration (F9).. If fact it did that... So the restoration started but when it shows a pop up "Restart now" the PC didn't do anything for like 30 minutes... So I decided to turn it off manually.. When the computer restarted, everything was a complete mess.. Grub tried to load an say like 100 errors.
F9 didn't work... Windows 7 didn't load... Ubuntu Netbook Remix didn't as well..
So I tried using the recovery DVD, but it just doesn't load....
I tried using the Windows 7 DVD to boot, and nothing... (The hard drive led doesn't turn off, but I've waitd like 2 hours and nothing).
I tried reinstalling Ubuntu and nothing..
I removed the hard drive and installed in a desktop computer... My idea was to open the 900ha's hard drive in windows (Using the desktop PC) and format it and merge the partitions... BUT!.. If the 900HAs hard drive is connected windows would not load... If I disconected it... Windows works just fine..
 
I REALLY don't know what to do...
I'm thinking that the hard drive was damaged somehow by grub??
 
Well, I managed to load Ubuntu using the live cd and it showed like 10 partitons (When I only had 3).. But now it doesn't load....
I really don't understand.
 
Thanks

---

### Post by s3a on 2009-11-07
When you install Windows after Linux, Windows makes changes to the Master Boot Record (MBR).

Follow this guide:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by manzdagratiano on 2009-11-07
Since you can boot with the LiveCD and it shows your hard drive, try using gparted to format it (with sudo). If that does not work, though I cannot really pinpoint what the issue is, if you can get into your laptop bios with your hard drive connected, you might be able to do a low level format if you have that option - this restores the hard drive to its factory settings. All your data however, will be lost beyond any form of recovery (not even by tools that can still recover some stuff after a normal format). The fact that the Live CD does show partitions and not nothing at all means (bless yourself at this time) that the hard drive is not short circuited (which could have been the case since your desktop does not boot when this HD is connected - happened to me once a long time ago and I lost a huge amount of data then; nothing irreplaceable though :D).

---

### Post by peikojose on 2009-11-07
> **manzdagratiano said:**
> Since you can boot with the LiveCD and it shows your hard drive, try using gparted to format it (with sudo). If that does not work, though I cannot really pinpoint what the issue is, if you can get into your laptop bios with your hard drive connected, you might be able to do a low level format if you have that option - this restores the hard drive to its factory settings. All your data however, will be lost beyond any form of recovery (not even by tools that can still recover some stuff after a normal format). The fact that the Live CD does show partitions and not nothing at all means (bless yourself at this time) that the hard drive is not short circuited (which could have been the case since your desktop does not boot when this HD is connected - happened to me once a long time ago and I lost a huge amount of data then; nothing irreplaceable though :D).
 
Thanks for your answer.
 
Could you explain to me how to use gparted to format the hard drive from the LiveCD?
 
I'm a linux newbie.. 
 
Thanks

---

### Post by nothingspecial on 2009-11-07
> **peikojose said:**
> Thanks for your answer.
 
Could you explain to me how to use gparted to format the hard drive from the LiveCD?
 
I'm a linux newbie.. 
 
Thanks

In the menu go system > administration > partition editor

Delete all your partitions and make 1 new one.

Try to copy all your data to some sort of removeable device first.

---

### Post by zman58 on 2009-11-07
Consider installing only Ubuntu on the machine. Use the entire hard drive  for Ubuntu and drop Windows completely. Egad you must have spent so many hours with this thing trying to deal with Windows you must be totally frazzed at this point. Dealing with Windows alone is a pain in the behind.

Why do you want to keep Windows around? It is like a ball and chain to deal with--dragging you down and keeping you from moving about.

One other point is that you should create a backup image your entire hard drive to separate media (external USB hard drive) before making dramatic changes to the system. Use a separate boot media Ghost recovery CD or USB stick to back it up before proceeding to operate on it. That way you can always get back to where you began if things should go awry. I'm sure you wanted to hear this now--sorry, but take this opportunity to learn from your mistakes so you don't repeat them. You should never mess up your computer if you have a stable backup image. This is especially important when you are dealing with Windows, which takes a lifetime to install and get working. Ubuntu, on the other hand, installs in minutes.

---

