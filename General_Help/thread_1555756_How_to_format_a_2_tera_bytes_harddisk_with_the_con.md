---
title: "How to format a 2 tera bytes harddisk with the console?"
date: 2010-08-18
forum: General Help
---

### Post by honeybear on 2010-08-18
Visibly the 2 tb are not supported by Ubuntu. cfdisk does not like my harddisk not fdisk. I am bit stuck ... 
I havent X11

---

### Post by Drenriza on 2010-08-18
why does ubuntu not support 2tb hdd,s?

the ext4 filesystem are more then capable then using disk space that size O.o

---

### Post by honeybear on 2010-08-18
> **Drenriza said:**
> why does ubuntu not support 2tb hdd,s?

the ext4 filesystem are more then capable then using disk space that size O.o

I tried for instance with cfdisk and visibly it doesnt want to create  my partition table:(

---

### Post by inameiname on 2010-08-18
I'd try gparted. I agree with Drendiza, that's weird as 2TB should be fine under Ubuntu.

---

### Post by coslo on 2010-08-18
> **honeybear said:**
> I tried for instance with cfdisk and visibly it doesnt want to create  my partition table:(

What's the error message of cfdisk? That could be helpful.

---

### Post by honeybear on 2010-08-18
> **coslo said:**
> What's the error message of cfdisk? That could be helpful.

I have to reinstall to get it. It didnt recognize my 2TB disks during install, or I did some other testing and it said that  GPT or GUID  were not recognized. I have to check again the msg

---

### Post by davrosuk on 2010-08-18
I agree with the other posters: its strange as it definitely should work. I've got a 6TB volume formatted!

---

### Post by LowSky on 2010-08-18
you could have recived a bad drive, it does happen.

---

### Post by honeybear on 2010-08-19
> **LowSky said:**
> you could have recived a bad drive, it does happen.

why not recognized?
During install the detection of drives goes blind, does not see the 2tb drives at all :( so not possibel to install on it :(

becasue of testing on several 2 to 3 drives similar, I believe one of them are ok. So it seems that cfdisk and fdisk are not well suited for large disks. However gdisk seems to give more resutls positive, but i am sitll in progress with it.

However gdisk is rather difficult to use compared to cfdisk.

Could be good that cfdisk works with 2tb disks, using gdisk or other.

---

### Post by oldfred on 2010-08-19
Most software assumes MBR or msdos style partitions. Gparted recognizes gpt and you mention gdisk which is for gpt parititons.

[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

