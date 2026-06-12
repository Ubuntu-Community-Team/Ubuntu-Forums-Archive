---
title: "Not Booting Ubuntu Netbook"
date: 2010-06-08
forum: General Help
---

### Post by boo557 on 2010-06-08
Ok so I was sick of windows 7, so I got ubuntu. I have an acer aspire one D250 with windows 7 starter, (its a netbook). I downloaded the NE iso and installed it to my netbook with a 4 gig sd card. I rebooted, heres the grub screen:
 
[CENTER]GNU GRUB version 1.98-1ubuntu5[/CENTER]
 
Ubuntu, with Linux 2.6.32-21-generic
Ubuntu, with Linux 2.6.32-21-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows Vista (loader) (on /dev/sda1)
Windows 7 (loader) (on /dev/sda2)
 
So I chose the first one, and the blinking line hangs there *forever.*
 
please help me out, I really would like to start enjoying ubuntu.
 
Other info:
 
CPU: Intel Atom CPU N270 @ 1.60GHz
 
BTW: Win 7 still boots fine :)

---

### Post by boo557 on 2010-06-09
Ok update, apperently I need to set that bios NX XD thing. I cannot find where. I booted windows 7 and found what I believe to be the setting, but now recovery mode ubuntu wont work. Please help :). 
 
UNE 10.04
32 bit system
 
If I find anything else I will post here. :lolflag:

---

### Post by boo557 on 2010-06-09
Aww come on, anyone? I dont think I can enable the NX XD thing on my system. Whats worse, I resized my HD to skim fifty gigs off of it, now I have an extra OS eating my space and I have yet to boot it! I tried installing the netbook remix today, but alas, I got an error after choosing to install side by side "ERROR!!: cannot access kernal blah and stuff blah" I'm not so much a happy camper right now and would like to get ubuntu remix installed (if possible.)
BTW: Couldn't there be a command to disable the need for protection? I rarely use my netbook for anything execpt working on an online game server. (which has a linux client :/ )

---

### Post by boo557 on 2010-06-11
Ok cool, I found my problems. (Ubuntu Netbook Edition Works great!) On windows 7, I went to system properties>system protection>processor (somthing like that)> advanced> enabled NX. Then I restart, chose ubuntu recovery mode, and login with the command line. (No security problems showing now :D. then run the "startx" command. Then enabled my wireless drivers, rebooted, and ran updates. Rebooted again, installed skype, then the Graal Online game client (used wine for Graal, installed the linux client with wine), and I'm good to go! I think ubuntu rocks, nice to have a change after 10 years of windows, (bleagh) :P :lolflag:

---

