---
title: "System Will Not Start - Missing Modules"
date: 2009-11-20
forum: General Help
---

### Post by allend on 2009-11-20
Apparently, I just know enough to be dangerous -- to myself.

Actually, I have played around with quite a few flavours of Linux for a while and usually all has gone well.  However...

I had 9.04 installed on a Gateway machine alongside the orginal Windows XP and all was well, except that the suspend did not work. The system would wind down, but the backlight stayed on and then the machine would not resume.  A reset was always required. 

I upgraded to 9.10 and all ran well, but since it ran so well and was in constant use, I decided to fix the sleep problem, so I Googled around. 

I suppose I should have looked here first, but I didn't and I wound up at [http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)

I noticed the versions discussed were not 9.10 (I can never get the version names), but I figured that what I saw did not look threatening and could be quite simple.  Although I have used apt-get before with various other Linuxes, I had always stuck to Synaptic on this Ubuntu machine.  The procedure looked straightforward and harmless and I decided to make an exception.  I followed the instructins and typed:

sudo apt-get install uswsusp
sudo s2disk       

The caution, " ## CAUTION: make sure data is saved for this test!" was a bit ambiguous, but I noticed that the system saved to disk.  

I can't recall if the machine went to sleep itself (it has a ten-minute timer until sleep) or I got the idea to restart. 

At any rate I was surprised to discover the OSs would totally not restart.

The machine starts booting when I choose Ubuntu (the default), but stopps with this message:

Gave up waiting for the root device. Common problems 77200cb02e6
 - Boot args (cat /proc/cmdline)
 - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/4677c91f-ea02-4295 (etc) does not exist. dropping to a shell!

Busybox v1.13.3 (Ubuntu 1.1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)  _
------------------------------------------------

so I typed...

(initramfs) pwd
(initramfs) /
ls
   (a long listing shows up)

(initramfs) cd /disk
/bin/sh: cd: can't cd to /disk
(initramfs)ls d*
dri:
card0

disk:
by-path  by-id   by-uuid  by-lable
(initramfs)
------------------------------------------------

When I try to boot to XP Pro, The system says, 

Windows could not start becasue the following file is missing or corrupt:
<Windows root>\system32\hal.dll.
Please re-install a copy of that file.

-------------------------------------------------

That looks like an obvious clue, whatever exactly it means.

Personally, it seems I have no idea what I am doing.  

I hope the fix is not too difficult (ie. possible). I like the way I had everything set up and was enjoying 9.10.

I have a bootable USB stick with 9.10 on it, if that helps.  

Otherwise, I can enter commands at a prompt.  Come to think of it, that is what brought me here.

Hope someone can steer me out of this.

TIA.

---

### Post by allend on 2009-12-17
Three weeks ago, I posted this request for some insight.  So far I see it has 85 views and no replies. Not one.

My Ubuntu installations sit useless and I have no idea what to do.  In the meantime, I have installed Windows 7 on three machines with no problems.

I had thought that Ubuntu might replace Windows for me, but I can see that day is a long way off.  

Over the years I have had plenty of problems with Windows, since I run many versions on many machines and also help friends with their problems, but they have always healed themselves or I have been able to easily find solutions in a short timeframe. I have NEVER had to reinstall Windows.  Not once.  

Not so with Ubuntu, so far, at least.

Is this probleminsoluable?  Did I not provide enough info?  Did I post it in the wrong place?  I am surprised I have had zero response, (not even the usual sort to tell me Linux rules and Windoze is a disease).

---

### Post by Yellow Pasque on 2009-12-17
Use a LiveCD and check your UUID's with:
```
blkid
```

---

### Post by allend on 2009-12-17
Thanks for the quick reply.  

I do have a live CD, but am unsure what the rest of your suggestion means.  Could you give me a little more detail, or point me to a resource which discusses what you suggest.

Again, thanks!

---

### Post by Yellow Pasque on 2009-12-17
> ALERT! /dev/disk/by-uuid/4677c91f-ea02-4295
I am thinking that you may have modified your partition somehow.

Boot into the LiveCD environment and post output from:
```
sudo fdisk -l
blkid
```

You should also fsck the partitions on that disk.

---

