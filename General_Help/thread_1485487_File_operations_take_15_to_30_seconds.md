---
title: "File operations take 15 to 30 seconds"
date: 2010-05-16
forum: General Help
---

### Post by hangfire on 2010-05-16
Sometimes while using Open Office, trying to open a file the dialog box takes 15 to 30 seconds of spinning balls until it shows me anything. Then changing a directory takes another 15 to 30 seconds. Visual feedback on selections take several seconds, and often I find myself a couple of subdirectories down from where I wanted to go due to caching of unacknowledged clicks.

My system is usually very, very fast, as one would expect from the specs. This problem happened, well, almost all the time with kernel 2.6.32-21-generic, now it just started happening again with 2.6.32-22-generic.

During these slowdowns, opening Dolphin reveals the same problem, exceedingly slow response. While this is happening, top shows the system is not busy, and the hard disk light is not flashing. Idle is over 90% and user and sys are basically nothing. The system is basically doing nothing while making me wait.

Very frustrated.

---

### Post by ryan858 on 2010-05-16
I'm having this problem as well... I thought it was my hard drive going bad... I also have random freezes that will disable all output, but user input and internal data are still (SLOWLY) processed until it comes out of the freeze (can be 1 second, 30 seconds, or or 10 minutes). But I think this is related to my hardware, unless someone else is having the exact same issue. But I definitely have slow file operations for seemingly no reason (unrelated to the freezes, although they do coincide sometimes).

---

### Post by hangfire on 2010-05-17
Please list your hardware... anything in common with mine?

Yes, a bad hard disk can cause performance issues. Usually you hear the head seeking on multiple retries. This should show up in the logs.

BTW My hard disk is less than a year old and comes through clean on a SMART check. There are no retry failures in any of the /var/log files.

-HF

---

### Post by hangfire on 2010-05-28
I suspect this is a 3-way interaction between: Using Dolphin to copy off of a USB camera drive, leaving Dolphin sitting in the destination directory, and using OpenOffice document insert image on that same directory.

Doing 2 out these three things has not been a problem.

-HF

---

### Post by hangfire on 2010-06-02
Is anyone home? Why do all my threads have no response? Do I have some forum stealth option clicked or something?

Hate to say it, but 10.04 is the worst release ever (in my experience), but I thought I at least had the support of the community... take a look at my threads, and my two launchpad bug reports... no response whatsoever.

-HF

---

### Post by TheDesertDragon on 2010-06-02
> **hangfire said:**
> Is anyone home? Why do all my threads have no response? Do I have some forum stealth option clicked or something?

Hate to say it, but 10.04 is the worst release ever (in my experience), but I thought I at least had the support of the community... take a look at my threads, and my two launchpad bug reports... no response whatsoever.

-HF

I absolutely agree with this statement. (Except 10.04 being a bad release - it's the best for me so far! :P ) Had 3 threads going about SDL issues (I couldn't use the volume controls in an SDL app), a driver problem with FGLRX 10.4, and the sound issue which concerning PulseAudio and Wine (turns out they forgot to add a certain file that makes PulseAudio work by picking up other sound architectures' streams).

No responses to any of them after 5 bumps in each over the course of a week.

Unfortunately I can't help with this. I have no clue about the Ext4 journaling file system - although you could try using another filesystem to install on? Afaik. Ubuntu can be installed even on an NTFS partition, so if that works for you, why not?

---

### Post by hangfire on 2010-06-02
Thanks for your sympathy.

> **TheDesertDragon said:**
> Unfortunately I can't help with this. I have no clue about the Ext4 journaling file system - although you could try using another filesystem to install on? Afaik. Ubuntu can be installed even on an NTFS partition, so if that works for you, why not?

Actually I'm running EXT3. I guess the default is 4? I usually manually edit the partition table on install to preserve my /home partition.

While it may be a file system issue, I am thinking kernel locking between usb file system and disk file system issues... just a guess, though.

-HF

---

### Post by supershin on 2010-06-02
You could always try running a liveCD and performing those tasks. If it takes less time then you know its not the hardware. It should take slightly longer to execute from a liveCD. 
Also running from a liveCD is like running a clean install so if it runs good from the cd then your config is bad. As for what in the config is bad i dunno.

---

### Post by radbrad32 on 2010-06-18
I have this issue too.  I've been patiently dealing with it since 9.10, hoping it would be fixed in 10.04, but no luck.  I've notice sometimes it doesn't happen the first time you open a file, but after that it does it pretty consistently every time.

Any clues?

BTW: I'm using Ext4, but I doubt this is it.  Also, it seems to be specific to KDE, otherwise the standard GNOME users would've chimed in and it would be fixed by now.

---

