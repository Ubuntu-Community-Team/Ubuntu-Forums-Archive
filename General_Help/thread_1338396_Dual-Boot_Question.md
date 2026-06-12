---
title: "Dual-Boot Question"
date: 2009-11-26
forum: General Help
---

### Post by Fernando Hernandez on 2009-11-26
Okay, so I'll be getting a new computer soon, and it comes pre-installed with Windows 7.  I have yet to try 7 for myself yet, and I'd like to, so I figured I'd ask this *before* getting it.  Currently I run Kubuntu Jaunty as my only OS on my laptop.  Initially I had a dual-boot set up with XP, and when I wanted to remove XP from my system the only way I knew how to do it was to completely format my machine, which also meant reinstalling Kubuntu and starting over after backing up my files.  When I get this, I'll either run Windows 7 as a single boot for a month or so before deciding whether I want to remove it or dual-boot, or I'll set up the dual-boot right away.  I don't want to set up a dual-boot with Kubuntu if I have no way of removing *just* 7, however, if I decide I don't want to keep it.  In other words, it's a pain to have to start from scratch with an OS when you're satisfied with your configuration, so seeing as I'll already have to do that once when I get the new machine, I don't want to end up, in a month, having to do it again if I want to remove 7.  

Is there a way to only remove the second OS without having to format the machine?  If there isn't, then I'll go without Linux for a month while I test 7.  I just want to know in advance before the machine comes and I set up a dual-boot, only to have to format and erase BOTH OSes if I decide to remove 7.  I'm satisfied with having Linux as my only OS on my laptop, and I'm considering getting 7 for my desktop anyways, but since the machine comes with it pre-installed already it'd be stupid of me to remove it without even testing it for myself for a little while.  So before I go ahead and set up my dual-boot, I thought I'd ask if there is any way to remove a secondary OS without having to format, so I don't need to rebuild my configuration *twice*. :)

---

### Post by emachnic on 2009-11-26
I guess you could probably use gParted and just resize the Linux partition to 100%. That's my initial thought though I've never tried it myself.

---

### Post by audiomick on 2009-11-26
Hallo.
it is not a problem to chuck out windows from a dual boot.
what will happen, is that your Grub2 i.e the bootloader, will get messed up, and you will have to reload it.

You should think about making a seperate partition in the Linux installation for /home. If you then have to re-install at a later date, you can simply re-mount it without fomatting, and all your data and configs will be retained.

Your Swap partition needs to be a bit bigger than your RAM, or the suspend and hibernate functions can't work

I have seen lots of suggestions for putting the whole Linux install in an extended partition. This is worth a thought. It seems like many win 7 installations already have 3 partitions set up, 2 for the system and a recovery partition which you can think about deleting. You can only have 4 primary partitions, so you are almost forced to use extended/logical ones.

It is a good idea to start the computer from the Ubuntu live cd before you do anything else. This will allow you to try out Ubuntu, and see if everything on the computer works properly. While you are at it, you can start the partition editor and have a look at your disc. The is no need to do anything at this point, except write down how it is partitioned so you can have a think about it before you install.

anyway, here's some reading:
(bear in mind, Ubuntu 9.10 uses the bootloader Grub2, I've included some links that talk about Grub. don't mix them up.)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

and about the "old" grub, used up to 9.04
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

to round off
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

and I assume you have read this:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

