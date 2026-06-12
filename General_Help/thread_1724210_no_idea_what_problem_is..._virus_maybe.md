---
title: "no idea what problem is... virus maybe?"
date: 2011-04-08
forum: General Help
---

### Post by magnetic651 on 2011-04-08
I just installed a fresh copy of Ubuntu and after running it for a few days I am having some strange issues.  First, I cannot access the Applications men.  When I click on the tab it highlights but I do not get a drop down menu.  Also, I am being told when I boot up that there is no hard disk space.  If I go to places->computer and check hard disk properties I am told that there is 66MB of space (I have a 640MB drive and only Ubuntu is installed).

What is going on?  I think I have a virus but I cannot install an antivirus because I "have no disk space" and can't access the terminal through applications.  I am going to try reinstalling but I was wondering if anyone else has encountered this or whether it is a simple fix.  Thanks.

---

### Post by plucky on 2011-04-08
> If I go to places->computer and check hard disk properties I am told that there is 66MB of space (I have a 640MB drive and only Ubuntu is installed).

Do you mean GB?

Open a terminal and post output of ```
sudo fdisk -l
df -h
```

The fdisk is lowercase L not a 1

---

### Post by Stephen Morgan on 2011-04-08
You can open a terminal without using the menu by press Ctrl-Alt-t or access the TTY with Ctrl-Alt-F1.

And I wouldn't worry about a virus.

---

### Post by Jouke74 on 2011-04-08
If you really have a 640MB drive than I am afraid that it is too small to effectively work with Ubuntu. I am surprised that you even got it installed because a CD iso is already 640 MB. If you mean GB something else is going wrong.

Please check the size of the logs. 

Please check the size of the partitions that Ubuntu is using, or is it the whole disk?

Please check the disk with the diskcheck utility (under administration).

Please post the output of the command: 
>sudo fdisk -l

---

### Post by mike555 on 2011-04-08
is this a "wubi" install?

---

### Post by Rubi1200 on 2011-04-08
> **mike555 said:**
> is this a "wubi" install?
Good point. We have seen this happening with Wubi installs before where the size given to the root.disk was too small.

@magnetic651; please confirm whether or not this is a Wubi install and run the commands posted by plucky.

---

### Post by magnetic651 on 2011-04-08
> **plucky said:**
> Do you mean GB?

Open a terminal and post output of ```
sudo fdisk -l
df -h
```The fdisk is lowercase L not a 1


No, I mean MB.  Now it says I have 44.5MB free.

I can't open a terminal because I can't access Terminal under Applications.

---

### Post by magnetic651 on 2011-04-08
> **Jouke74 said:**
> If you really have a 640MB drive than I am afraid that it is too small to effectively work with Ubuntu. I am surprised that you even got it installed because a CD iso is already 640 MB. If you mean GB something else is going wrong.

Please check the size of the logs. 

Please check the size of the partitions that Ubuntu is using, or is it the whole disk?

Please check the disk with the diskcheck utility (under administration).

Please post the output of the command: 
>sudo fdisk -l

Sorry, the drive is 640GB.  But it says I have 44.5MB free now.

How do I check the size if the logs?

Under Disk Utility, it tells me my disk is 640GB, capacity actually 622GB, one big partition.  

Here is the output:

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007e427

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       75605   607288320   83  Linux
/dev/sda2           75605       77826    17841153    5  Extended
/dev/sda5           75605       77826    17841152   82  Linux swap / Solaris

---

### Post by magnetic651 on 2011-04-08
also:

pip@pip-CM5570:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             571G  542G   45M 100% /
none                  2.9G  252K  2.9G   1% /dev
none                  3.0G  188K  3.0G   1% /dev/shm
none                  3.0G  216K  3.0G   1% /var/run
none                  3.0G     0  3.0G   0% /var/lock
pip@pip-CM5570:~$ 


what is "wubi"??

---

### Post by magnetic651 on 2011-04-08
Looked it up.  No, I didn't use Wubi.

---

### Post by plucky on 2011-04-09
> /dev/sda1 571G 542G 45M 100% /

You have something filling up your hard drive.It could be a rogue log file or another thing could be a backup job gone wrong.

Checkout this [Thread](http://ubuntuforums.org/showthread.php?t=898573&highlight=drs305+Trash) to find what is filling up your hard drive.

Good Luck

---

