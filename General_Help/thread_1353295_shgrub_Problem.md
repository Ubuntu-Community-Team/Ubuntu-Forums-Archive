---
title: "sh:grub Problem"
date: 2009-12-12
forum: General Help
---

### Post by TheHL2Guy on 2009-12-12
I installed Ubuntu from Windows today, and it worked very fine until i changed something with the partition (i'm bad at english, i mean like C:/ or D:/) So after i was done on the internet i turned off my computer. Then some hours later i turned it on again to check my Facebook. Everything went fine until i was booting Ubuntu.

It was a command line or something like this:

                   GMU GRUB version 1.87''beta4

( Minimal BASH-like line editing is supported. For the first word, TAB lists
possible command completions. Anywhere else TAB lists possible
device/file completions. )

sh:grub> _


Can anyone help me?
Windows does not work either, and i can't boot the CD in Bios.
It's a normal CD-R with Ubuntu 9.10 and a autorun.
And i have tried every commands i can like boot ubuntu 2.0.0.16 kernel32 and startup Ubunt etc...


Please respond me :)

---

### Post by battleshipterry on 2009-12-30
I have same problem with 2 different pcs. just reloaded this pc but laptop has same error when trying to boot ubuntu.

GMU GRUB version 1.97~beta4

[ Minimal BASH-like line editing is supported. For the first word, TAB lists
possible command completions. Anywhere else TAB lists possible
device/file completions. ]

sh:grub>


running 9.10 ,duel booting Win XP,on both pcs

FYI I did not do any changes to partition

---

### Post by theKay on 2010-01-06
Gentlemen, if you used wubi, it is a documented bug and a workaround patch is presented below:

[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169?comments=all](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169?comments=all)

Hope this helps. 

Cheers

---

### Post by robomorris on 2010-02-10
Were you able to fix this? If so, how. I am not technical!!!!!!!!!

---

### Post by JustinRez on 2010-03-08
I'm having this problem now, as well, using Windows 7.  I ran an update and I no longer have any options to use previous versions.  It just brings me to the 'sh grub' prompt. I referenced the link provided but the people on that board clearly have a very good understanding of the command line interface and linux.  I have neither, though I've been able to use Ubuntu exclusively for a few weeks now (and I've had to figure a few things out :)

They say something about installing grub via that interface or being able to boot by typing something at that interface.  I'm wondering, if I reformat the partition I have dedicated to ubuntu in a linux-friendly format (not sure which that would be) instead of ntfs, would that fix this problem after I reinstall?

Thanks!

---

### Post by InFamousD on 2010-04-08
Hey Guys Dont know if this will help or if any of the thread previous have answered the problem.

I tried wubi, to install both ubuntu and kubuntu and had this same problem, then i tried to do it from CD, and still had the same problem here is my set up

p4 550
2 hd 40g/80g
1g Ram
Windows XP on main 80g
Nvidia graphics 128mb

Anywho, Every time I installed it would boot the first time, then the next time I would run the system my XP kernal would be missing a root file or Unix wouldnt load and I would get 

sh:grub

I tried some of the solutions people gave and typed mad codes into correct this nothing worked. Until I did some exploring of my own

My chipset is configured of HP/Dell parts (its a old desktop I threw together off peoples junk) WORKS GREAT by the way, but my point is This worked for me

Ubuntu has already been installed at this point but failed on the first restart boot up -
After debugging the Windows XP (cause installing ubuntu seemed to ruin my root files) installation, after fixing windows i restarted my cpu. In the set up bios screen I made sure my OS choice was listed as WinXP/Other, then once it loaded I popped my ubuntu cd in btw this is all 32-bit and ran it LIVE inside windows, I then turned my cpu off (just by shuting it down improperly) and went back into setup then in the BIOS i listed my OS as Linux/other/NT saved changes and put Hard Drive to be the first to boot. Saved settings then BOOM it worked! Ubuntu loaded, I downloaded all the upgrades and it asked if I wanted to keep grub1 or install the new grub. I selected the new Grub, now I have no problems. Hope this helps.

For all the people who listed codes, Thank You for the help but this will not work. You cannot direct a files or find files with no Kernal present that so sudo/cat/ and unix stuff simply wont work. You have to trick the cpu into thinking its booting XP because your partitions are NTFS or windows kernals, by makeing the change in the BIOS the cpu doesnt know what its doing so it boots the active Live Ubuntu OS that you were trying out when you d/l your upgrades it then recognizes hey theres a problem, do you want grub1 or 2? Then you choose, after you d/l everything take the cd out and restart, and presto the failed install of Ubuntu is now fixed and recognized, I believe my shutting down the cpu imporperly might left the temp memory untouched since it wasnt dumped and it might have something to do with it. Again I am an amateur who used to work with Tandys and windows 98 Dos, and just got back into this stuff, but hey it worked for me : ) hope you have the same luck I did. 

:P:popcorn:

---

### Post by TheHL2Guy on 2011-01-15
[SOLVED]

Well sorry for late reply. I just got a new CD (WINDOWS) from my neighbour and installed Windows XP. Now i have a HP Mini 110 with Windows 7, HP QuickWeb OS (very good) and Ubuntu Desktop (newest now)

So how did i fix it? FORMAT :D:D:KS

Thanks for the help anyway ;)

---

