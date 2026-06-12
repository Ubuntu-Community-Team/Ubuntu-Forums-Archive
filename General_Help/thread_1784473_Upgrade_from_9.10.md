---
title: "Upgrade from 9.10"
date: 2011-06-17
forum: General Help
---

### Post by BigD77 on 2011-06-17
Hello,

   I upgraded from 9.10 to 10.04.  9.10 was stable as a rock.  However, when I upgraded to 10.04, my laptop seems to go buggy.  After about 5 minutes, the screen goes blank, followed by vertical lines and some text flashing, never to return.  At that point I have to turn off the laptop, then restart it.
   Needless to say, I am a bit dissapointed after having such a stable version in 9.10.

My laptop is a Dell Inspiron 1100, with 512 MB of RAM.  I dual boot with Windows XP.

---

### Post by xavi787 on 2011-06-17
> **BigD77 said:**
> Hello,

   I upgraded from 9.10 to 10.04.  9.10 was stable as a rock.  However, when I upgraded to 10.04, my laptop seems to go buggy.  After about 5 minutes, the screen goes blank, followed by vertical lines and some text flashing, never to return.  At that point I have to turn off the laptop, then restart it.
   Needless to say, I am a bit dissapointed after having such a stable version in 9.10.

My laptop is a Dell Inspiron 1100, with 512 MB of RAM.  I dual boot with Windows XP.

I got the same problem but with 9.10. In my case the problem was with my wireless card and overheating problems.

---

### Post by wildmanne39 on 2011-06-17
> **BigD77 said:**
> Hello,

   I upgraded from 9.10 to 10.04.  9.10 was stable as a rock.  However, when I upgraded to 10.04, my laptop seems to go buggy.  After about 5 minutes, the screen goes blank, followed by vertical lines and some text flashing, never to return.  At that point I have to turn off the laptop, then restart it.
   Needless to say, I am a bit dissapointed after having such a stable version in 9.10.

My laptop is a Dell Inspiron 1100, with 512 MB of RAM.  I dual boot with Windows XP.Hi, if this is only after it is not used for five minutes go into screen saver and set it not to come on the power management and set it not to spin down drive or to put monitor to sleep.

---

### Post by BigD77 on 2011-06-18
> **wildmanne39 said:**
> Hi, if this is only after it is not used for five minutes go into screen saver and set it not to come on the power management and set it not to spin down drive or to put monitor to sleep.

I tried doing that, but it went right into the blank screen, followed by the vertical lines and the flash of some words on the screen too fast to make out.

I just happened to be on wireless at the time, so that may be a problem as well.  When I upgraded to 10.04, I was on a wired network and didn't have this problem.  BTW, the laptop does not have built in wireless, but has a PCM/CIA slot wireless card.

I almost wish I could roll it back to 9.10, but I know that's not possible.

Don't know if this helps, but it's a Pentium 4 circa 2002 with 512 MB RAM (Max for that model)  :confused:

---

### Post by BigD77 on 2011-06-18
I wonder, would upgrading to 10.10 help any?

---

### Post by wildmanne39 on 2011-06-18
> **BigD77 said:**
> I wonder, would upgrading to 10.10 help any?
Hi, I do not know 10.04 is suppose to be the most stable release.

---

### Post by BigD77 on 2011-06-18
Since I downloaded and put 10.10 on a disc, I might try doing a fresh install of that.

---

### Post by BigD77 on 2011-06-22
Well, I went into Windows XP and deleted the partitions that held Ubuntu 10.04 and tried to load Ubuntu 9.50 from a USB drive.  The last time I did this was back about a year ago when I first tried to upgrade to 10.04 and the laptop was TOTALLY buggered up.  9.50 was the last stable version that I ran on here.  However, I loaded it from a 9.04 CD back then, and upgraded to 9.10. 

It loaded nicely, bu when I re-booted to run it from the hard drive, I got: "Can't find 139cb424-a9b8-40f8-a406-eccb4487f724. Hit any key to continue."  Won't load from the hard drive.  

Right now, I am at a loss of what to do.

---

### Post by haqking on 2011-06-22
> **BigD77 said:**
> I tried doing that, but it went right into the blank screen, followed by the vertical lines and the flash of some words on the screen too fast to make out.

I just happened to be on wireless at the time, so that may be a problem as well.  When I upgraded to 10.04, I was on a wired network and didn't have this problem.  BTW, the laptop does not have built in wireless, but has a PCM/CIA slot wireless card.

I almost wish I could roll it back to 9.10, but I know that's not possible.

Don't know if this helps, but it's a Pentium 4 circa 2002 with 512 MB RAM (Max for that model)  :confused:

Just for future reference, whenever there is an update, i dont do the update as i prefer a fresh install of the new version.
I use clonezilla to clone my existing system and in the even the new version dont work i just clone my original system back, its kind of like the ghost software that use to be popular.

Also if you have seperate partitions mounted as / /home /usr etc etc then it is easy and not too much hassle to get your data back etc, but always make sure you have back ups and back ups of backups ;)

---

### Post by gordintoronto on 2011-06-22
I would try 11.04 from a LiveCD. If it seems to work, install it.

---

### Post by beew on 2011-06-22
Don't do upgrade especially when you have something old like 9.10. A fresh install is the way to go.

---

### Post by BigD77 on 2011-06-23
> **gordintoronto said:**
> I would try 11.04 from a LiveCD. If it seems to work, install it.

Oh, I have 9.10 on a USB stick.  Worked well from there.  So I deleted the partitions for 10.04 like I did in the past, then tried to load it from the USB.  Loaded fine, but when I rebooted, I got an error, somthing like "Kernel panic" and wouldn't load.  I then re-deleted the partitions while in Windows XP.  Then when I re-booted, I got another error (grub error) and XP wouldn't load!

So I had to go back, load 9.10 again, and again I got the error that 9.10 will not load, but I could load Windows.

Is it because I was loading from a USB drive and not from a CD?

---

### Post by BigD77 on 2011-06-23
> **beew said:**
> Don't do upgrade especially when you have something old like 9.10. A fresh install is the way to go.

When you do a fresh install, how do you go about it?  Do you delete the old partition, or do you run the CD?  I tried to run the USB stick without deleting the partition first, but the installer would force me to leave about 2-3 GB of space for the previous install on Ubuntu, in this case, the unstable 10.04.  It was then that I deleted the partition and tried to start over.

---

### Post by BigD77 on 2011-06-23
When I tried to launch Ubuntu from the hard drive, the message I got was:

error: couldn't find file.  Kernel panic-not suncing VFS.
Unable to mount root fs on unknown block (0,0)
[0.688351] Pid 1:comm: swapper not tainted 2.6.35-22 generic #33Ubuntu
[0.688351] Call trace

---

### Post by gordintoronto on 2011-06-23
> **BigD77 said:**
> ...I tried to run the USB stick without deleting the partition first, but the installer would force me to leave about 2-3 GB of space for the previous install on Ubuntu, in this case, the unstable 10.04.  

I don't understand what you are saying. Three gigs is nothing on modern hard drives.

I don't delete the old root (/) partition, but I always format it. If you have data there, back it up first!

---

### Post by dFlyer on 2011-06-23
Backup your data you want to keep and install over the old ubuntu partition. I've been do that since 6.06 without a problem. Even if you keep you /home on a separate partition back it up before you install. If your going to use 11.04, I'd start with a clean /home and restore files to it.

---

### Post by wildmanne39 on 2011-06-23
Hi, you should start a new thread with your new problem with a title like grup error will not boot, that way you can get more help on this particular problem. The people that help with boot problems dont know you are having boot problems so you are not getting the help from them, I am learning boot issues but I am not an expert that is why you should start a new thread on the topic.

---

### Post by BigD77 on 2011-06-26
> **wildmanne39 said:**
> Hi, you should start a new thread with your new problem with a title like grup error will not boot, that way you can get more help on this particular problem. The people that help with boot problems dont know you are having boot problems so you are not getting the help from them, I am learning boot issues but I am not an expert that is why you should start a new thread on the topic.

Thanks.

---

