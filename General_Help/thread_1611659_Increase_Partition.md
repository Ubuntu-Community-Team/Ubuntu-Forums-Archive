---
title: "Increase Partition"
date: 2010-11-02
forum: General Help
---

### Post by timeoutmode on 2010-11-02
HI,,

I have been trying to increase my Ubuntu partition but Gparted Live cd won't let me.. The unallocated space is before my extended partition where my ubuntu partition is placed. Gparted pops up saying it is likely that I won't be able to boot after increasing the extended partion because it will move the Ubuntu partition. Please help.

---

### Post by timeoutmode on 2010-11-02
Hi Guys,

I have to ask you guys now after 1 hour of searching the answer for my problem. I want to increase my Ubuntu partition but Gparted live cd won't let me. It says that if I did so it is likely that I won't be able to boot anymore since I moved the partition. Here is my partition:

Windows 7
Unallocated Space
Extended Partition:
    Ubuntu Partition
Primary Partition

As you can see I'm try to increase the extended partition by extending it the the left, where the unallocated space is. Then, Gparted pops up saying what I mentioned above. Here is the thing,, should I proceed? and still extend it? or that's a no-no? Has anyone tried this?

---

### Post by timeoutmode on 2010-11-02
bump

---

### Post by timeoutmode on 2010-11-02
bump

---

### Post by cpmman on 2010-11-02
Patience - unpaid volunteers here.

Please click the boot_info_script in my signature and post the RESULTS.txt (in quotes) back here.

A screenshot of your Gparted might help as well.

I may not be able to help but someone more knowledgeable/experienced probably will.

---

### Post by TheAnachron on 2010-11-02
Have you backed up your data?

I have done the exact same thing 2 days ago and everything was fine.
But you should seriously be careful with this. Better make sure to have all data (or at least the important data) backed up before doing this.

---

### Post by s.fox on 2010-11-02
Threads merged. Please do not create duplicate threads. Thank you.

---

### Post by Mark Phelps on 2010-11-02
Have you tried expanding your Extended partition to the left, first?  You will have to do that before extending your Ubuntu partition.  And, since you're not creating any new partitions, that should not affect booting in any way.

---

### Post by timeoutmode on 2010-11-02
> **TheAnachron said:**
> Have you backed up your data?

I have done the exact same thing 2 days ago and everything was fine.
But you should seriously be careful with this. Better make sure to have all data (or at least the important data) backed up before doing this.


finally, so nothing happend? though gparted said it is likely that you won't be able to boot? thanks

---

### Post by timeoutmode on 2010-11-02
> **Mark Phelps said:**
> Have you tried expanding your Extended partition to the left, first?  You will have to do that before extending your Ubuntu partition.  And, since you're not creating any new partitions, that should not affect booting in any way.


that's the thing.. i wanted to extend it to the left side but gparted alerted me possible unbootable partition..

---

### Post by timeoutmode on 2010-11-02
@anarchon.. i'm backing up my whole disk through "Macrium Reflect" in my Windows 7. It can detect my Ubuntu partition. how about you? what did you use in imaging your system?

---

### Post by TheAnachron on 2010-11-02
Hi, I just used my external HDD and copied everything to it.
I don't like any backup programs, because most are either slow or buggy. 

I like simplicity. And I can always copy back data from my hdd, while for your backup you will need the software.

---

### Post by timeoutmode on 2010-11-02
> **TheAnachron said:**
> Hi, I just used my external HDD and copied everything to it.
I don't like any backup programs, because most are either slow or buggy. 

I like simplicity. And I can always copy back data from my hdd, while for your backup you will need the software.


How about the OSes? you won't be able to back them up.

---

### Post by TheAnachron on 2010-11-02
Wait, what? You can surely backup operating systems. Just copy all the files, the hidden and the protected ones (needs a few parameters more, but who cares).

That is the same that those programs do, just with a GUI.

---

### Post by alphaamanitin on 2010-11-02
> **timeoutmode said:**
> How about the OSes? you won't be able to back them up.


I just dd the drive.  One to one clone.  Don't mess up your if and of though or you won't have any data at all.

AlphaA

---

### Post by timeoutmode on 2010-11-02
thanks everyone.. i'm backing up my whole drive now.. i will try to extend my partition tomorrow.. goodluck to me..

---

### Post by timeoutmode on 2010-11-02
thanks everyone.. i'm backing up my whole drive now.. i will try to extend my partition tomorrow.. goodluck to me..

---

