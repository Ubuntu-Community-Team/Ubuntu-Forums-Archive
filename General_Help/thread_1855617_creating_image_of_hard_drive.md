---
title: "creating image of hard drive"
date: 2011-10-06
forum: General Help
---

### Post by YigalB on 2011-10-06
I would like to create image file of the hard drive, sometimes of a Linux machine, sometimes of a windows machine.
The target of the image is to allow duplicating the whole content into another computer (same hardware).

Is there a single utility that can do that? 
Do I need separate utility for windows/Linux?

Any recommendation?

---

### Post by Basher101 on 2011-10-06
Windows has a built-in utility for that (at least windows 7 does, what windows do you want to duplicate?)
as for Linux i use a VERY user friendly tool called Remastersys, it creates a Bootable .iso of your Linux distro with all the Programs and Data. A small warning tho, this program has some space limitations. Because the created .iso is bootable it must fit a DVD, thus not be bigger than 4 GB in total. I was able to create a Bootable .iso that was 2 GB big, compressing my 10 GB full install of Ubuntu (with alot of programs and music) so i guess the maximum it can compress is 20 GB. So as long as you keep only programs on it, its the best tool you can get. For storing Files i would recommend some External Media (USB sticks, external HDD)

---

### Post by YigalB on 2011-10-06
For Windows, I need to duplicate XP & 7.
for both OSs, I need non-limited size, to be stored on USB disk which will be used as source when duplicating.

---

### Post by c-1000 on 2011-10-06
Try Clonezilla, its a great piece of software.

---

### Post by collisionystm on 2011-10-06
> **c-1000 said:**
> try clonezilla, its a great piece of software.

+1 +1 +1 +1 +1 +1 +1 +1 +1 +1 +1 +1 +1 +1

---

### Post by Basher101 on 2011-10-06
I tried to install clonezilla, somehow completeley failed at it...does it simply dump the whole data on other media so you can just copy it back, or does it create its own data format for the copies?

---

### Post by collisionystm on 2011-10-06
> **Basher101 said:**
> I tried to install clonezilla, somehow completeley failed at it...does it simply dump the whole data on other media so you can just copy it back, or does it create its own data format for the copies?

Run the Clonzezilla live cd, have a usb hard drive ready to copy the hard drive image to

---

### Post by Basher101 on 2011-10-06
so it will make a 1:1 copy of all the partitions? can i not copy only a single partition, lets say my ubuntu partition only? and how do i restore a partition after having made a copy of a partition?

---

### Post by spiky001 on 2011-10-06
Will this help  [http://geekyprojects.com/cloning/how-to-use-clonezilla-tutorial/](http://geekyprojects.com/cloning/how-to-use-clonezilla-tutorial/)

---

### Post by collisionystm on 2011-10-06
> **Basher101 said:**
> so it will make a 1:1 copy of all the partitions? can i not copy only a single partition, lets say my ubuntu partition only? and how do i restore a partition after having made a copy of a partition?

i think you can choose what partition you want to copy. but then again, it might want to copy the entire drive. You may need to copy your whole drive, and mess with it to remove Windows ( or other dual boots ) and then do a clonezilla again.

Once you have the disk copied to your usb harddrive, you just plug the harddrive into another computer with the clonezilla live cd and choose to restore

You can also do a network version where the clonezilla live cd will just pull the image from a server hosting the drive image

---

### Post by Basher101 on 2011-10-06
Thanks to the link spiky001 provided, i see it cannot restore a partition without erasing the whole hard drive. Since now i was restoring my linux partitions with the Live .iso after making some formatting to the partitions with Gparted and made the usual install where all my files and programs that were taken to the custom .iso get also installed and could keep all my windows files and such. That wont be possible with clonezilla as i see it...

also...you need multiple steps to clone your hard drive with clonezilla. I am able to create a live .iso with just 2-3 Clicks...
so i guess Remastersys is a bit more user friendly. All the cloning aside, it is quite nice to have a custom Live CD that has certain programs other Distros out there do not have (for example you have a fresh install of ubuntu, install programs for boot failure scans and repair programs and such...and then make a Live .iso from it. It has multiple uses like this, or you can give the live .iso as a Live USB stick to friends so they can check out your Linux with all the nice themes and features you use..)

---

### Post by collisionystm on 2011-10-06
> **Basher101 said:**
> Thanks to the link spiky001 provided, i see it cannot restore a partition without erasing the whole hard drive. Since now i was restoring my linux partitions with the Live .iso after making some formatting to the partitions with Gparted and made the usual install where all my files and programs that were taken to the custom .iso get also installed and could keep all my windows files and such. That wont be possible with clonezilla as i see it...

also...you need multiple steps to clone your hard drive with clonezilla. I am able to create a live .iso with just 2-3 Clicks...

It would have to erase the hard drive. What exactly are you trying to do? Create multiple dual boot computers?

---

### Post by Basher101 on 2011-10-06
Not me. I just wanted (and did so) to make a complete restore of my Ubuntu without having to erase Windows 7 all the time as it takes ages to reinstall windows, all the programs and updates...this was for the time when i messed alot aroung with Ubuntu before i settled with a partition Setup i liked and such. Remastersys is very useful tho, i can imagine making a custom Distro as a teacher for some students with programs ubuntu usually would not have...you would have everything pre-configured.



I dunno if the OP is just reading everything or just busy and not looking at the thread. You should ask the OP for more information. Tho as i read in the first post, the OP wants to copy one Pre-configured Windows XP, Windows 7 and ubuntu to another machine(s)

---

### Post by viperdvman on 2011-10-06
Couldn't you use Clonezilla to copy Ubuntu from one partition to another on the same hard drive? Or copy it from a partion of Hard Drive A to a partition on Hard Drive B... without overwriting everything on Hard Drive B?

---

### Post by Jouke74 on 2011-10-06
You can also restore a single partition with Clonezilla. There is one but, the free partition you are cloning to needs to be the same size as the partition to be restored (or bigger).

You can also select multiple parttions or a whole disk to clone with clonezilla. The filesystem on disk does not matter much, NTFS (Windows) works as well as EXT (Ubuntu).

You backup (USB) disk needs to have enough space.

Leaves the question if the same Windows License is going to work on multiple pc's...

---

### Post by viperdvman on 2011-10-06
It does make me a bit nervous trying this out. As long as I can copy my Ubuntu partition from its (e.g. 30GB partition) to a free partition that's the same size or bigger without deleting my Windows and Swap partitions, then I'll go for it.

---

