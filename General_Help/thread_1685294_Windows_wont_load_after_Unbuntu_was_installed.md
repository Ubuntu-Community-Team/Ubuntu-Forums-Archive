---
title: "Windows wont load after Unbuntu was installed"
date: 2011-02-10
forum: General Help
---

### Post by CentriFightr on 2011-02-10
I loaded Ubuntu 10.0.4 on my HP laptop and it works fine.  However, i went to load my Windows 7 partition and it crashes every time i go to load it.  I see the partition just fine in Linux, i can access the files and all that stuff.  However, i went to the windows installer and tried to find my C: drive and it says it is not ready.  Also when i use the disk, it says it cant find any drives on my computer so i cant just reinstall windows because it cant find a hard drive.  I have tried fixboot on windows and that didnt fix it.  I was going to try reformatting the entire disk and seeing if windows can find the hard drive but im not even sure if that would work.

The blue screen i get on windows when i boot is 0x0000007B.  I have tried so many things and nothing has worked.  If you have any idea on how i can fix this, please help.  Thanks.

---

### Post by Mark Phelps on 2011-02-10
You didn't say how you installed Ubuntu.

One of the really BAD things about the 10.10 installer is that it no longer has the "use largest free space" option from the previous installers.  Instead, you have to mess around with manual partitioning, and if you're not extremely careful, you will accidentally reformat your MS Windows partition in the process.

To see what partitions you now have on your drive, open up a terminal window in Ubuntu and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  If you don't see any NTFS partitions, then you basically overwrote your Win7 install with Ubuntu.

---

### Post by CentriFightr on 2011-02-10
I used the Windows partition shrinker and used it to split off a small chunk off the end of the main partition.  Then I installed Linux onto the new smaller partition I made.  I used the fdisk function and it shows the original windows partition as SFS.  So now what do I do?  

I guess that would explain why windows cant load but that doesn't really explain why a windows boot disk cant find a hard drive..

---

### Post by oldfred on 2011-02-10
You tried to create more than 4 primary partitions in windows. It then automatically converts to a LVM - logical volume manager the is proprietary to windows. Offically windows says you have to totally backup delete SFS partitions and create new basic partitions and restore data. Not all windows tools seem to work with its SFS system and Linux does not in most cases.

SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec)
Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)
Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)
Not sure if in "free" version, but older version had it & was free see 4.2:
[http://www.partitionwizard.com/help/convert-dynamic-disk-to-basic-disk.html](http://www.partitionwizard.com/help/convert-dynamic-disk-to-basic-disk.html)

---

### Post by Bucky Ball on 2011-02-10
> **Mark Phelps said:**
> 

One of the really BAD things about the 10.10 installer ...

> **CentriFightr said:**
> I loaded Ubuntu 10.0.4 on my HP laptop ... 

OP using 10.04 LTS. ;)

---

### Post by claire14 on 2011-02-10
> **Mark Phelps said:**
> You didn't say how you installed Ubuntu.

One of the really BAD things about the 10.10 installer is that it no longer has the "use largest free space" option from the previous installers.  Instead, you have to mess around with manual partitioning, and if you're not extremely careful, you will accidentally reformat your MS Windows partition in the process.

To see what partitions you now have on your drive, open up a terminal window in Ubuntu and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  If you don't see any NTFS partitions, then you basically overwrote your Win7 install with Ubuntu.

i have installed Linux on 3 diffrent Laptops with no problems .
the last laptop i  installed Linux on was with Linux Pendrive and that wiped windows 7 ,  does anyone  how to get youtube to run on a 64bit  hp laptop , also my terminal wont let me type my password when it asks for it , i need proper instructions to install flash or i'm wipeing my laptop and restoring windows

thanks to anyone who knows how to fix Linux

---

### Post by Bucky Ball on 2011-02-10
> **claire14 said:**
> i have installed Linux on 3 diffrent Laptops with no problems .
the last laptop i  installed Linux on was with Linux Pendrive and that wiped windows 7 ,  does anyone  how to get youtube to run on a 64bit  hp laptop , also my terminal wont let me type my password when it asks for it , i need proper instructions to install flash or i'm wipeing my laptop and restoring windows

thanks to anyone who knows how to fix Linux

Welcome. You would be much better off posting a new thread with a descriptive title about your problems and as much detail as possible. You will get more specific help. It is difficult to figure two problems at once (and you have several). ;)

---

### Post by claire14 on 2011-02-10
:) thankyou  ,  i found the flash player instructions thats ok now , i just need my dvd loader files for my dvd's  where should i post for that , my terminal might not be fixed though , flash auto extracted for me lol , youtube play's   yay

---

### Post by CentriFightr on 2011-02-10
Oh my goodness, thank you Jesus, it worked.  I used the diskpart option in the windows boot command line and found that my disk was allocated as a dynamic disk so windows didn't like that.  I just used the convert basic command and am now currently installing windows back onto my computer.  Thank you very much for your help.  Now I do have one more question... if I install Linux back on after Windows, will it do the same thing to the disk that I just fixed?

---

### Post by Bucky Ball on 2011-02-11
Use manual partitioning. The Windows disk will be clearly visible (NTFS format). Just leave it alone and create three partitions, something like:

/ = where your OS lives, 20Gb more than enough;
/home = where your personal data and settings live, large as you like;
/swap = 2Gb or same size as installed RAM if you want to hibernate.

That's it. The install should pick-up your Windows and add it to the grub list. 10.04 LTS (long term support) is supported until April 2013 and is stable. You will probably get a smoother ride. ;)

---

### Post by oldfred on 2011-02-11
+1 on Bucky Ball's suggestion. You may have to create an extended partition to hold logicals for Ubuntu.

Use windows tools for windows, & Linux tools for Linux. Just do not try to create extra partitions for Linux with windows as Windows will not create compatible formats anyway. Use gparted or the installer to create partitions for Ubuntu.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

