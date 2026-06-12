---
title: "Is it possible to assign a /boot partition after installation"
date: 2012-07-31
forum: General Help
---

### Post by yoreei on 2012-07-31
Hi, I just installed Xubuntu 12.04 64 bit. The first few times I tried to install the OS the installer freezed because of partition misconfiguration. that said - I am a new Linux user and have probably made a mistake while assigning /boot /home /var /tmp their own partitions. So I installed everything to root and the rest ran fine. 
Enough intro. Here is the question:
I want to move /boot /home /var and /tmp to their own partitions. Is that possible? How do I do this?
Thank you in advance!

---

### Post by dino99 on 2012-07-31
here is how to do installation:

[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

no needs to break the ubuntu default logic ):P

---

### Post by oldfred on 2012-07-31
I only suggest moving /home to another partition and even that does not have to be done.

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

If you really want to move the other partitions I think it is the same procedure. But moving /boot will also require a reinstall of grub2's boot loader.

Herman goes the other way and does not even create a separate swap.
Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by Cheesemill on 2012-07-31
Is there any good reason you want to have /boot /var and /tmp on different partitions?

---

### Post by trulteree on 2012-07-31
> First of all, excuse me for my bad english, but it is not my native language.  I must say that until now I have worked with Win2000/Xp. Long time ago I worked with Xenix and in the last 2 month sometimes with Ubuntu.  Now I have brought a new PC with 320Gb HD and 4 Gb RAM, and I wish to built a dual boot system, with Win7 and Ubuntu.  After doing some search on google and see some partitions scheme, I have thought the following schema:    ==================================================  =================================================  Primary part. 1:  Linux /boot, size 500 Mb, type   ext3       Primary part. 2         :  Win7 disk C:\, size 80 Gb, type      NTFS; for OS and Win programs   Primary part. 3         : Reserved                 500 Mb      ext3; reserved for future /boot of another distro.   Extended partition: Logical part. 1: Win7 disk E:\, size 60 Gb     , type NTFS;  Only data ( D:\ is CD ) Logical part. 2: Space reserved       63 Gb                Reserved for E:\ or \home increment or another distro.  Logical part. 3: Linux /home            , size 60 Gb, type ext3     ; Only data ( and /usr/locale )      Logical part. 4: LVM volume, size 60 Gb so initially subdivided: / 30 Gb, /tmp 15 Gb,  /var 15 Gb Logical part. 5:  /swap, size 6 Gb    , type: swap     Note: 1) /boot is the first, so if I need to increment C:\, I have to move only E:\ and partition 3 2) Partition 3 may be user for another linux distro 3) About swap: I have followed the Red Hat rule ( if ram >= 4Gb then swap = 2 + RAM; 4) About /home: I want a partition that I can backup with an utility like Norton Ghost for example. 5) About /, /tmp, /var: I want separate the temporary files from real OS files. LVM should give me the    possibility of change the partitions size when I will have more experience.   Can it work ?  What do you think about ?  Any suggestion will be highly appreciated.   Best regards, Simone  youve hit the nail on the head

---

### Post by yoreei on 2012-08-03
> **Cheesemill said:**
> Is there any good reason you want to have /boot /var and /tmp on different partitions?
Actually, the only reason I tried placing them on their own partitions is because I had never done so before and I was curious.

I managed to install Xubuntu the good old way - everything in /
Thank you all for your answers and sorry for the late reply - I was thinking I had already replied.
Maybe I'll have to do a bit more research before trying this type of installation again.
I find oldfred's links very helpful, thank you!

---

