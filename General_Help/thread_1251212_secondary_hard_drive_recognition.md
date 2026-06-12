---
title: "secondary hard drive recognition"
date: 2009-08-27
forum: General Help
---

### Post by tw11 on 2009-08-27
Hello, I'm new to the forums but not really* that *new to Ubuntu. I've had it installed on my laptop for several months. Anyway, I've decided to install it alongside Win xp pro on my desktop but have run into some problems.
 
Before installing, I had two hard disk installed in my computer. One 250gb and one 750gb. the 750gb was used for media storage so xp was installed on 250gb one. Both drives are SATA. I wanted to maintain my 750gb one purely for media since it runs a bit slower.
 
I decided to install ubuntu on the 250gb one, giving it a ~30gb partition. the installation went fine but when the computer restarted, grub did not appear. i searched around on the forums and found a way to [restore grub]("http://ubuntuforums.org/showpost.php?p=1308395"). the method still didn't work however and i suspected that my secondary hard drive may be at fault.
 
i shut down my computer, disconnected the 750 drive, rebooted, reinstalled ubuntu, and now grub, along with both ubuntu and xp worked.
 
So i shut down my computer again, plugged in my drive, and started my computer in XP. When I go to My Computer, the drive still appears (drive H:) but when I click on it, it says "The disk in drive H: is not formatted. Do you want to format it now?" My computer obviously still sees the drive but for some reason, it can't access it. If I click properties, it says that the type is RAW instead of ntfs.
 
I know my drive is still OK and that the data is all in tact but I don't know how to recover it. I used TestDisk and it worked on recovering some of the data but none of it is sorted or named.
 
My guess is that when I installed ubuntu, it changed the MBR or something. I was thinking of maybe using fdisk from within ubuntu to try to change the format of the drive to ntfs but I'm not sure how to use it or if it'd even work.
 
I don't care if I can't access the drive in ubuntu but I want to access it in windows. Any suggestions??
 
(I don't know if this makes any difference, but the 750 disk was also a "dynamic" drive)

---

### Post by tw11 on 2009-08-27
bump. anyone?

---

### Post by scouser73 on 2009-08-27
Here is a tutorial on mounting an external hard drive: [[COLOR="Red"]**Mount External Hard Drives**[/COLOR]]("https://help.ubuntu.com/community/Mount/").

---

### Post by tw11 on 2009-08-27
Thank you but the hard drive isn't external. it's internal using the SATA interface

---

### Post by SuaSwe on 2009-08-27
Can you access the drive in Ubuntu? Just to give us an idea of whether it's working.

Ubuntu was installed on the 250GB drive, along with Windows, is that right? So the 750 one is for storage only? Does it have an OS installed on it?

---

### Post by scouser73 on 2009-08-27
> **tw11 said:**
> Thank you but the hard drive isn't external. it's internal using the SATA interface

The tutorial I mentioned also shows you how to mount internal SATA drives.

---

### Post by tw11 on 2009-08-27
> **SuaSwe said:**
> Can you access the drive in Ubuntu? Just to give us an idea of whether it's working.

Ubuntu was installed on the 250GB drive, along with Windows, is that right? So the 750 one is for storage only? Does it have an OS installed on it?
 
Yes, both windows and ubuntu are installed on the 250 one. the 750 is purely for storage and has no OS on it.

I'm not sure if I can access the drive in Ubuntu. I can't see it anywhere though. I can see the rest of my 250gb drive (the C: drive) but nothing about the 750. how can I look for it in ubuntu?

---

### Post by tw11 on 2009-08-27
if I do fdisk -l, I get this which shows the 750 drive as being of type SFS, is there any way I can change that?

```
xxxxxxx@xxxx:~$ sudo fdisk -l

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       91201   732572001   42  SFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       26506   212909413+   7  HPFS/NTFS
/dev/sdb2           26507       30401    31286587+   f  W95 Ext'd (LBA)
/dev/sdb5           26507       30235    29953161   83  Linux
/dev/sdb6           30236       30401     1333363+  82  Linux swap / Solaris

```

---

### Post by SuaSwe on 2009-08-27
Formatting it would do it, but you'd lose your data if you did that. Frankly I've personally never heard of an SFS file system, and I also don't think this has anything to do with MBR; if your 750GB hard drive didn't have an OS on it, it shouldn't even enter into the whole boot sequence to my knowledge.

Have you tried mounting the Windows drive via Ubuntu, like so:

[http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/](http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/)

? 

A long shot but getting hold of your files like that would at least be more convenient. You'd probably still have to move them all off the hard drive and reformat it though, sadly. Before you do though, I'd wait for some of the real experts to have their say! :D

---

### Post by tw11 on 2009-08-27
yes, i tried that. using fdisk, i was able to reset the partition table for the disk. the problem, as i've now found out, was that the disk was a dynamic disk so i guess just changing the partition table isn't enough now. i also can't mount it unless it's in the correct format.

---

