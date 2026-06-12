---
title: "free up hd space for dual boot"
date: 2009-10-26
forum: General Help
---

### Post by scottac on 2009-10-26
alright. I am currently running a mythbuntu installation on my main home machine. I have been screwing around with linux mint 7 on my laptop and want to set up a dual boot on my main home machine.  

I currently have 35GB of space on my system drive that I can use for this installation.  the only problem is that I don't know how to create a partition in which to install mint onto.  

I have gparted installed but don't know where to go from there.

any and all help is appreciated

---

### Post by alphaniner on 2009-10-26
If you are thinking of resizing a partition I will abstain, but it might help your cause to post some more information, such as the output of **sudo fdisk -l**, and a screenshot of gparted showing the layout of the drive you are going to use.

---

### Post by scottac on 2009-10-26
```
mythbackend@mythbackend-desktop:~$ sudo fdisk -l
[sudo] password for mythbackend: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000dd6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001   83  Linux

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x437193c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         486     3903763+  82  Linux swap / Solaris
/dev/sdb2   *         487        9039    68701972+  83  Linux

```

---

### Post by razorboy5 on 2009-10-26
insert the LiveCD
then open gparted
 
everything should be simple from there on

---

### Post by scottac on 2009-10-26
ughhhh..

Thanks.....

But I am looking for a little more help.

1.) Why would I need to insert the live disk to open up gparted when I have gparted installed under ubuntu already. 

2.) everything should be simple huh.  WOW.  Thanks for the help.  

Any serious responses will be greatly appreciated.  I am not a complete linux noob but have never tried to dual boot two different linux distributions so I might need a little more help than razorboy5 is offering.

thanks again

---

### Post by scottac on 2009-10-26
> **alphaniner said:**
> If you are thinking of resizing a partition I will abstain, but it might help your cause to post some more information, such as the output of **sudo fdisk -l**, and a screenshot of gparted showing the layout of the drive you are going to use.

And yes I think I need to resize the partition.

---

### Post by alphaniner on 2009-10-26
I'm assuming that /dev/sdb2 is your Ubuntu install partition, and is the partition you want to resize.  If so, you will need to use a live CD because you can't resize an active partition (and you can't unmount /).  But that's all I can help you with.  I've never done any partition resizing.

Edit: One more thing, be sure to backup your valuable data before attempting a resize.

---

### Post by scottac on 2009-10-27
OK. I am going to resize my partition first thing in the morning after I back everything up.  

Has anyone done this before? I would really like sort of a step by step so as to not screw anything up.  I have never resized anything using gparted before so I am a little apprehensive about all this. 

Any pointers would be greatly appreciated...

---

