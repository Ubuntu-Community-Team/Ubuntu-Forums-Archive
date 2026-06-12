---
title: "&quot;Routine check of drives&quot; freezes Ubuntu startup"
date: 2009-07-29
forum: General Help
---

### Post by techiewannabe on 2009-07-29
I am very much a "newbie." I've had Ubuntu on my laptop, a Compaq Presario R3000, for about three weeks.

My trouble is this. When I start up my system, I get a message saying, "Routine check of drives..." My system looks like it starts to do a check but then freezes. (I have to reboot the system and press the escape key to avoid this "routine check.") If I understand it correctly, this procedure is meant to check the status of my hard drive. (The hard drive is brand new. I installed it exclusively for the Ubuntu program that I installed.) I've looked up this problem on the Ubuntu forums and have tried some of the suggestions but none seem to work. It may be my own ignorance, or it may be the suggestions are not relevent to my system.

If anyone out there has any ideas, I'd appeciate it.

Thanks.

Techiewannabe

---

### Post by Tman5293 on 2009-07-29
To stop disk checks all together go to the terminal and type the following command:

sudo tune2fs -c 0 -i -0 /dev/sda1

If you want to do forced checks less often modify the -c parameter accordingly by changing the 0 to a higher number

Example:

sudo tune2fs -c 50 -i -0 /dev/sda1

---

### Post by synapsys on 2009-07-29
> **techiewannabe said:**
> If I understand it correctly, this procedure is meant to check the status of my hard drive. 

This procedure checks the integrity of the file system. It doesn't check to see if your hard drive is bad (bad blocks) but that the ubuntu file system is ok. By default I believe it is set to run every 30 boots or so. You can change this if you wish, as mentioned above.

---

### Post by techiewannabe on 2009-07-31
Thanks, Tman5293 and Synapsys. I'll try your suggestions.
Techiewannabe

---

### Post by 1401gazza on 2009-09-05
Hi guys
I've been having the same problem, the routine drive check freezes anywhere between 9 - 19% and then after about 10mins my laptop just shuts down.
If there's a problem surely simply stopping the drive checks won't rectify the problem just hide it.I would rather be able to have the checks run their course.....Any hints or ideas would be grateful...but please, not too technical...

---

### Post by techiewannabe on 2009-09-06
Hi 1401:
I'm afraid that I never solved this problem. I ended up reinstalling the OS!
Tom

---

### Post by pastalavista on 2009-09-06
I would try running the fsck from the recovery mode to see if it will complete successfully.

---

### Post by 1401gazza on 2009-09-07
> **pastalavista said:**
> I would try running the fsck from the recovery mode to see if it will complete successfully.


Well, you talking to a complete novice here so how would I go about doing that?

---

### Post by CatKiller on 2009-09-07
> **pastalavista said:**
> I would try running the fsck from the recovery mode to see if it will complete successfully.

Isn't the drive still mounted in recovery mode? fsck shouldn't be done on a mounted drive. Running it from the live cd might be a better plan.

```
sudo fsck /dev/sd*xn*
``` will do it, where *x* refers to the device, and *n* refers to the partition number. So, for example, if you only had Linux on the first drive, the partition might be /dev/sda1.

```
sudo fdisk -l
``` will tell you what's on each partition. You only want to run fsck on a partition that has a Linux filesystem.

---

### Post by 1401gazza on 2009-09-08
Sorry catkiller...I said complete novice...that lot may as well have been written in Latin

---

### Post by CatKiller on 2009-09-08
> **1401gazza said:**
> Sorry catkiller...I said complete novice...

And how does one stop being a novice? By learning and doing, of course.

Boot from the install cd, copy-and-paste the second command if you don't already know how your partitions are laid out, then run the first command.

It's hardly rocket science.

---

### Post by winotree on 2009-09-08
I followed these instructions [http://ubuntuforums.org/showthread.php?t=1255523](http://ubuntuforums.org/showthread.php?t=1255523) -- especially the wiki article -- and moved the drive check function to shutdown.  It just seemed a more appropriate time to do something like that.  Maybe this is an option for you, too?  ;)

---

