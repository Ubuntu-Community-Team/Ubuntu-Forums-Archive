---
title: "Input/Output Errors On Boot"
date: 2011-12-14
forum: General Help
---

### Post by ImmortalZecred on 2011-12-14
Hello,

I'm not at all new to Ubuntu (I've been using it since 8.10, and have used Ubuntu to dual-boot with Windows on several machines as well), but I've come across something unusual.

I was encountering some problems relating to Windows 7 with my graphics card, so I decided to downgrade to Windows XP. I wiped all of the drives, including my installations of Ubuntu and Windows 7, and reinstalled Ubuntu 10.04 with WinXP. The only thing that I did differently this time was install an extra swap partition on the secondary hard drive, for faster read-write access to that drive (as I had read about in an article).

Now, when I boot into Ubuntu, I get input/output error messages. They scroll way too fast for me to catch exactly what they say, so I enabled the boot log file- The boot logs show NOTHING about the errors, even though I can see them flash by when the system boots (just before the purple Ubuntu screen shows). It doesn't seem to affect system performance at all though, which I find unusual.

Has anyone seen this, and does anyone have a solution for it- Or at least another way I could log what happens during the boot so I can post more information?

Relevant system info-

HD1: Boots Ubuntu 10.04 LTS // One swap partition exists on this drive, 10 GB of space (8GB of physical RAM)
HD2: Boots Windows XP SP3 // One swap partition exists on this drive, 10 GB of space

Linux bootloader installed to HD1, which is listed as BIOS primary boot drive.

Ubuntu partition is ext4 format, Primary Partition, at Beginning of drive. Both swaps are listed as end of drive.
XP partition is NTFS, primary.

-Z

---

### Post by supercheetah on 2011-12-14
What do you get from *dmesg*?  Have you checked */var/log/messages*?

---

### Post by ImmortalZecred on 2011-12-16
Hi Supercheetah,

I checked the dmesg log, and here's what it contained. You'll notice that these errors are very near the bottom, and there are quite a few of them. The first one I saw began at address 11.374538. Search for that and you'll find them all by scrolling down from there. I had to enclose the text file in a .zip file because it exceeded the maximum size for a .text file on the forum. 

Thanks for the help. I appreciate it.
-Zecred

---

### Post by supercheetah on 2011-12-17
Do you have a CD/DVD in the drive when booting up?  *Sense Key : Illegal Request* seems to happen sometimes when a bad CD is in the drive, and the kernel can't read from it.

Other than that, I can't see what else might be going on.  What about */var/log/messages*?

---

### Post by ImmortalZecred on 2011-12-17
After examining my hardware, I found out that (as you suggested) the CD drive was the problem. I had a CD in there while booting several times, and it was a blank DVD+R. I noted that in /var/log/messages, the drive that was causing the problem was sr0. Checked into my disk utility, looked at the specs, and voila! The CD drive was, indeed, registered as address sr0.

I'll be sure to be careful about this. Thank you very much for your help!
-Zecred

---

