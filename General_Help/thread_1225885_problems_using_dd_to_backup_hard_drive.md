---
title: "problems using dd to backup hard drive"
date: 2009-07-29
forum: General Help
---

### Post by blahblahblah5038 on 2009-07-29
I am new to linux, and am a current XP user, but I have grown skeptical of microsuck after seeing Vista and the slightly less disgusting Windows 7 release canidate.
 
I recently bought a new 1 TB hard drive to replace my old 120 GB hard drive (too small). I installed xp on the TB drive, as well as a lot of the software I use on a daily basis, and I would like to make a backup copy, so I can periodically do a quick reload of the machine. 
 
I have been trying to use dd to copy from one drive to the other. Here's what I have done so far:
 
1)booted the computer from a xubuntu live cd
 
2) mounted both drives to see which one was sda and which was sdb, the TB is sda, and the 120 GB is sdb.
 
3)sudo dd if=/dev/zero of=/dev/sdb bs=4k
 
4)sudo dd if=/dev/sda of=/dev/sdb bs=4k conv=noerror,sync
 
5) wait a long time, and see an error pop up when dd runs out of space on the 120GB disk.
 
Problem happens when I try to boot from the other disk, I get a read error message that tells me to try again by restarting the computer.
 
Is there a way to make this work? I have been considering that there may be problems taking a large drive and putting it on a small one.
 
Are there any utilities that may do this better?  
 
Edit: Also, is there a way to make dd ignore blank areas on the disk?  would gzip be able to do it by compressing the blank spaces?

---

### Post by nothingspecial on 2009-07-29
Have a look at [[COLOR="Magenta"]clonezilla[/COLOR]]("http://www.clonezilla.org/")

---

### Post by Kraut~salat on 2009-07-29
it won't work like that. For the dd-method you need two of exactly the same HDDs. You cannot use two of different sizes. 
dd will copy eveything on the harddrive, including partioning information. That will be incompatible between the two HDDs hence the error at boot-up.

I also recommend to generally use dd on unmounted devices only.

---

