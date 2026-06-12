---
title: "Downloading trouble"
date: 2009-10-21
forum: General Help
---

### Post by oxubasas on 2009-10-21
I was trying to download a file and i keep getting an error that says i don't have enough disk space. It says i need to remove or delete unnecessary files. I don't know which disk space it it talking about or what files to remove.

---

### Post by Giblet5 on 2009-10-21
> **oxubasas said:**
> I was trying to download a file and i keep getting an error that says i don't have enough disk space. It says i need to remove or delete unnecessary files. I don't know which disk space it it talking about or what files to remove.

You paid for, or configured your system to have, X disk space. You used it all - probably downloading stuff.

That is OK. You're supposed to.

If you keep everything you download, and never delete anything, then one day (that would be today, for you) your X-space system will run out of space.

Click the "Places" menu. Select "Home Folder".

That's all the stuff you've been collecting.

Decide what you do and don't want anymore. Delete what you don't want.

Then empty your trashcan. (Right click the trashcan icon, select "Empty Trash")

---

### Post by oxubasas on 2009-10-21
This is the message of the error screen i am getting.

There is not enough room on the disk to save /tmp/pL_Ve0b+.doc.part.
Remove unnecessary files from the disk and try again, or try saving in a different location.

I look at the home file as you suggest. Most of my files are empty. I just got this laptop from a friend and it is recently formatted. 6 out of 40gb of hard drive is for window XP. The rest I just partitioned for ubuntu today. I dont understand. The file i was trying to download is eclipse ide for java. Anyways while it was downloading it locked up. I tried to cancel it but it wouldn't go away. I assumed it just hadn't been erased so i started another download. I don't know if the second on finished or if the first on got erased. I think this may be what is holding up my disk space from letting me download anyother files.

---

### Post by fluffman86 on 2009-10-21
go to Applications > Accessories > Terminal and type:

sudo fdisk -l

and post the output here.

Edit: Also, go to System > Administration > Computer Janitor and allow it to cleanup your computer.  If something is stuck in /tmp, rebooting may help, or press alt+f2 and type "gksu nautilus" to remove unnecessary files from /tmp

---

### Post by oxubasas on 2009-10-21
Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

also when i tried to run cleanup janitor and nautilus the both failed

Failed to run computer-janitor-gtk as user root.

Unable to copy the user's Xauthorization file.

---

### Post by fluffman86 on 2009-10-21
Sorry, I should have pointed out that in

sudo fdisk -l

the last letter is a lower case L.

Also, from the terminal, try 

sudo apt-get autoremove

---

### Post by OpenGuard on 2009-10-21
Let us know the output of the following command.

```
df -h
```

---

### Post by oxubasas on 2009-10-21
the sudo fdisk-l command wasn't found.


brian@brian-laptop:~$ sudo fdisk-l
[sudo] password for brian: 
sudo: fdisk-l: command not found
brian@brian-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
brian@brian-laptop:~$

---

### Post by oxubasas on 2009-10-21
df-h command not found

---

### Post by OpenGuard on 2009-10-21
> **oxubasas said:**
> df-h command not found

Copy and paste what I wrote. [COLOR=Gray]df -h[/COLOR], not [COLOR=Gray]df-h[/COLOR] ( whitespace missing ),

---

### Post by oxubasas on 2009-10-21
Filesystem            Size  Used Avail Use% Mounted on 
 /dev/sda5             2.6G  2.5G   19M 100% / 
 tmpfs                 249M     0  249M   0% /lib/init/rw 
 varrun                249M  124K  249M   1% /var/run 
 varlock               249M     0  249M   0% /var/lock 
 udev                  249M  152K  249M   1% /dev 
 tmpfs                 249M   84K  249M   1% /dev/shm 
 lrm                   249M  2.2M  247M   1% /lib/modules/2.6.28-15-generic/volatile 
 overflow              1.0M  1.0M     0 100% /tmp 
 /dev/sda1              35G  6.8G   28G  20% /media/disk

---

### Post by OpenGuard on 2009-10-21
What's inside /dev/sda6 ? Can you resize your Ubuntu partition ( Gparted ) ?

---

### Post by oxubasas on 2009-10-21
im not sure how to tell you what is in dev/6. i am a beginner. the only things that i have on here is windows xp and ubuntu. no pics, videos, music, word docs, etc.
what do you recommend i resize them to. I had it take up all the free space when i installed ubuntu

---

### Post by OpenGuard on 2009-10-21
Ok, well, the easiest way would be to boot into Windows, use a tool like Partition Magic and resize it's partition ( eg., -10Gb ). After that, extend your Ubuntu partition and this problem ( no space left ) should disappear.

---

### Post by oxubasas on 2009-10-21
do i need to download partion magic because i haven't heard of it. Also is it not all already partitioned to ubuntu since i had it take up all the free space when i  installed it.

---

### Post by Don1500 on 2009-10-21
> **oxubasas said:**
> do i need to download partion magic because i haven't heard of it. Also is it not all already partitioned to ubuntu since i had it take up all the free space when i  installed it.

Partition magic is an .ISO that you will download and make a Live CD to boot from (like what you did to get Ubuntu). You will boot into a chopped down linux distro with a number of good utilities on it. You have to do it this way because you should not play with your hard drives while you are using them to run your machine.

Be sure to read the instructions and help files. It's not that hard but you can lose much data (if not all) if you do something you shouldn't

---

### Post by oxubasas on 2009-10-21
thank you all for your help I will give it a try tomorrow and update you. look for an update in the afternoon est time.

---

### Post by 3rdalbum on 2009-10-21
> **oxubasas said:**
> do i need to download partion magic because i haven't heard of it. Also is it not all already partitioned to ubuntu since i had it take up all the free space when i  installed it.

Your Ubuntu partition is only 2.6 gigabytes.

When the installer says "free space" it means "unpartitioned space"; it doesn't gather up all the bits of your Windows partition that aren't being used and make Ubuntu use that. Not unless you actually use the "Resize partition" option and drag the little slider on the bottom bar graph to the left.

You'll need to use Partition Editor (on the live CD), or the Gparted live CD, or some other partitioning tool to make your Windows partition smaller and your Ubuntu partition bigger.

---

