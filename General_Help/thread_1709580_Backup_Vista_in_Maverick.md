---
title: "Backup Vista in Maverick?"
date: 2011-03-18
forum: General Help
---

### Post by WhyCali on 2011-03-18
I've managed to hopelessly muck up my Vista partition, and have tried everything I've found for two days now.  My next thought is to somehow backup, reinstall vista and restore from the backup.  Is there some way to create a virtualhd (virtualbox) or use Wine to run the Vista backup utility?

---

### Post by alphaamanitin on 2011-03-18
What did you do and what have you tried?  TestDisk is a good program that can recover files, partitions, and I don't know what else.  I recovered a drive with it after I deleted the partition and reformatted the entire HD.  TestDisk will run in Windows and Linux.  

AlphaA

---

### Post by WhyCali on 2011-03-18
I have my original Vista Ultimate x64 install DVDs.


[LIST]
[*]All four steps on [http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)
[*]process in Microsoft's support article: [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[/LIST]
And a few other things I found in forums, including using diskpart to make sure the correct partion (disk 0, partition 1) was active:  diskpart, select disk 0, select partition 1, active

I then reinstalled Ubuntu 10.10 (32-bit) and set the hard drive (there's only 1) for the bootloader.  It now boots straight into Ubuntu 10.10 (x32) with no problem.  There's a Vista option on the Grub2 menu, but of course it takes me to the same black screen with a blinking cursor.

Any ideas appreciated!

Mike

---

### Post by alphaamanitin on 2011-03-18
I am still not quite getting your setup and the issue.  I assume you either had Vista and Ubuntu installed on the same drive, or on separate drives and after reinstalling Ubuntu Vista will not load?  

Please post the output of this command ```
sudo fdisk -l
```

Place the output in code tags.  That is the # button in advanced reply mode or simply type [ CODE ] OUTPUT OF COMMAND [ /CODE ]  Just remove the spaces in the [ ] .

AlphaA

---

### Post by blueridgedog on 2011-03-18
you should be able to backup essential files from the partition and re-install.  Can you still mount the partition while booted into Linux?  Posting the fdisk output requested will help.

---

### Post by WhyCali on 2011-03-18
Sorry, I'm not by the computer now, so I can't do an fdisk -l.

This is what I have... let me know if you still need the fdisk -l.

```

/dev/sda1 - NTFS 110.48GB Boot (Vista Ultimate x64)
unallocated - 1.5GB
/dev/sda3 - ext2 37GB (Ubuntu 10.10 32bit)
/dev/sda4 - linux-swap 4 GB

```

Thanks!  Mike

---

### Post by grahammechanical on 2011-03-18
Do not take my word for it but I do not think that it is possible to backup any Microsoft Windows operating system from Ubuntu or any Linux distribution. Even inside of wine.

What you can do from Ubuntu and Linux is access the Windows drive/partition and make copies of your important data. You can do this because the Linux developers have built a system that reads and writes to the file systems that Microsoft uses. Windows uses do not have this feature in their operating system.

Because you have Vista install DVDs you can then re-install Vista. Afterwards you will not be able to boot into Ubuntu. So, run the Ubuntu live CD and in a terminla type sudo update-grub2

regards.

---

### Post by blueridgedog on 2011-03-18
The best you can do is mount your windows drive, copy over essential files then re-install.

---

