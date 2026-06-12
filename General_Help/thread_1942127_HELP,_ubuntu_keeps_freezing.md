---
title: "HELP, ubuntu keeps freezing"
date: 2012-03-16
forum: General Help
---

### Post by limjix on 2012-03-16
Good day,

I am on Ubuntu 11.10 and I have had it on my computer for quite sometime, however now I notice that the OS randomly freezes without any particular cause. None of the keyboard buttons or mouse works and I have to press the power button to reboot

Here are some situations,
1. I was reading a pdf file and scrolling and the whole thing just freezes.
2 I was watching youtube and some other tabs were open on google chrome, the computer freezes, the sound on youtube will look itself for a few times then completely stop. EG: "This machine here.....This machine here......This machine here.....stop"
3. I was using the unity browser and it just froze.

Basically, every day, my OS will freeze up at least 3 times. Any idea what I should do??

Thanks!

---

### Post by d3ngar on 2012-03-16
When you say freezing...

Can you get into the command line prompt (CTRL + ALT + F1)?

If so, you could check: dmesg.
It might tell you (us) a bit more.

Then you also don't need to power off, but reboot, eg: sudo reboot.

Or, you could just restart your display manager: sudo service gdm restart

Lastly, if your system really freezes, try checking the RAM. You should be able to do that from the grub menu. I think you will have to hold space to get in there now.

---

### Post by limjix on 2012-03-16
I haven't tried getting to the terminal,

However, I have already run MEMTEST and it seems that it said my RAM passed.

---

### Post by jerrrys on 2012-03-17
Try Unity 2d and see if problems persist

---

### Post by Hylas de Niall on 2012-03-17
I don't think it's Unity.
I had the exact same problem with 11.10. I tried switching to Gnome Shell and it still kept happening. Hardware all checked out fine, and all the advice i got on here didn't reveal anything awry with my installs (i tried installing from three seperate sources of 11.10).
I switched back to 10.10 and the issue was gone.

---

### Post by jerrrys on 2012-03-17
You should have a system monitor in unity.  Use it to monitor swap to see if its getting used up.

---

### Post by limjix on 2012-03-17
> **jerrrys said:**
> You should have a system monitor in unity.  Use it to monitor swap to see if its getting used up.

My System Monitor says it is using 0% out of 0 bytes. Is the 0 bytes a problem??

---

### Post by Helen McCall on 2012-03-17
Check your logfiles. Especially syslog and dmesg.

The most common cause I know for this kind of thing happening is if you have some bad I/O errors repeating.

Many things can cause this including a hard disk beginning to fail, or the disk controller, or a loose or badly fitted cable etc etc.

launch your logfile viewer and look for syslog.

Also launch a terminal and issue the command 
   dmesg | less
That will pipe the output of dmesg through the pager "less" and allow you to page through it.

---

### Post by BertN45 on 2012-03-17
> **limjix said:**
> My System Monitor says it is using 0% out of 0 bytes. Is the 0 bytes a problem??

I do not know how much memory you have, but if it is less then say 1 GB this could be your problem. You do not seem to have an active SWAP partition and if the memory fills up your system will freeze or programs will crash. If you close all programs you do not need the next minute and if you reduce the number of tabs in the browser, the freeze might occur less frequently.

It will not occur with 10.10, because that one uses far less memory, also Unity 2D will use less memory. The easiest thing is to re-install and to make sure you have a SWAP partition on the main disk. What size Hard Disk and RAM do you have?

---

### Post by limjix on 2012-03-18
> **Helen McCall said:**
> Check your logfiles. Especially syslog and dmesg.

The most common cause I know for this kind of thing happening is if you have some bad I/O errors repeating.

Many things can cause this including a hard disk beginning to fail, or the disk controller, or a loose or badly fitted cable etc etc.

launch your logfile viewer and look for syslog.

Also launch a terminal and issue the command 
   dmesg | less
That will pipe the output of dmesg through the pager "less" and allow you to page through it.

Okay i got the log files open, what should I be looking for??

> **BertN45 said:**
> I do not know how much memory you have, but if it is less then say 1 GB this could be your problem. You do not seem to have an active SWAP partition and if the memory fills up your system will freeze or programs will crash. If you close all programs you do not need the next minute and if you reduce the number of tabs in the browser, the freeze might occur less frequently.

It will not occur with 10.10, because that one uses far less memory, also Unity 2D will use less memory. The easiest thing is to re-install and to make sure you have a SWAP partition on the main disk. What size Hard Disk and RAM do you have?

I have a 320 gb hard disk and a 2 gb RAM. However, previously I tried dual booting my laptop with windows. When i used windows CD to partition my drive to make space for it, it messed up the partition tables, I saved the tables using an app, now Gpart does not recognise the partitions on my HD.


The problem just happened again, i tried CTRL + ALT + F1 until F5, nothing happened. However, when i close my laptop screen, the screen actually turns off and when I open it again ,it turns on.

---

### Post by 2F4U on 2012-03-18
> **limjix said:**
> My System Monitor says it is using 0% out of 0 bytes. Is the 0 bytes a problem??

No, that just means that the OS can keep anything in RAM at the moment. This is good since RAM is much faster than swap.

---

### Post by BertN45 on 2012-03-18
With 2GB of memory you should not have that many problems with the missing SWAP partition. It looks like the partition tables are messed up and as soon as Linux wants to use the SWAP partition the system hangs. That is consistent with what Gpart(ed?) is saying. 

I suggest to download the "gparted live cd" and use that to check and repair the partition table. You need the gparted live cd, because the partitions are otherwise locked by Ubuntu. If you are lucky the live-cd will detect the problem and offer to correct it. Make sure that the SWAP partition is of the type "SWAP". Don't forget to back-up the data of the whole disk incl. the windows data that you can't afford to loose.

If repair is not possible use the gparted live cd to get at least 15GB free space for Ubuntu and re-install Ubuntu using that free space.

---

### Post by jerrrys on 2012-03-18
Lets look at your video.  Open a terminal and enter:

sudo lshw -C display

lspci -nn | grep VGA

and please post

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

