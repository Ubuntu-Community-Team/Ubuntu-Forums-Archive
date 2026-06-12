---
title: "Recovery disk"
date: 2010-10-30
forum: General Help
---

### Post by limjix on 2010-10-30
Hi guys, i want to ask, i have customized my ubuntu alot and have installed many programs.

I want to ask is it possible to create a recovery disk that is able to reinstall my whole OS just the way it was when i created the disk, all programs and settings just the way it is, in the event that my system has a problem??

If so, how to do it?

Thank you!!

---

### Post by matsuzine on 2010-10-30
I would suggest using disk cloning software.  [Clonezilla]("http://clonezilla.org/") is a good option.  I've also used [partimage]("http://www.partimage.org/Main_Page") before.

Then you can restore from the disk image.

---

### Post by papibe on 2010-10-30
I also recommend Clonezilla, you can find reviews and tutorials on youtube if you find the interface intimidating.
Regards.

---

### Post by limjix on 2010-11-01
does clonezilla create a WHOLE copy of your hard disk?

meaning if you have 20gb on the system partition , the backup will be 20 gb??

is it better that i copy my whole drive into a hard disk and in the even something goes wrong, i format the partition and paste back the whole hard disk backup?

---

### Post by HiImTye on 2010-11-01
I would just copy my home folder to a disk. you can always add the programs you want but setting everything up takes time.

maybe take a snap shot of the programs you have installed

---

### Post by Megaptera on 2010-11-01
If you want to make a CD/DVD backup, then have a look at Remstersys:

[http://ubuntuforums.org/showthread.php?t=1514043](http://ubuntuforums.org/showthread.php?t=1514043)

very useful!

---

### Post by indytim on 2010-11-01
For partition level imaging applications, your choices with an ext4 filesystem are:

fsarchiver (as part of SystemRescue CD (my favorite),
Clonezilla and RemasterSys.

Partimage is no longer an option for current operating systems as it does not support ext4.  Remastersys will make an image of your operating system partition, but that's all (not applicable for data type of partitions).

Fsarchiver has become my weekly backup engine for backing up 17 partitons.  The list includes NTFS, ext3 and ext4 partitions.  It is run from within the SystemRescueCD so you don't get into the issue of backing up actively mounted partitions.  I have successfully restored 30G partitions using the app and it's image files.

Here's a couple of links if you're interested in checking it out further.

[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

[http://www.fsarchiver.org/Main_Page]("http://www.fsarchiver.org/Main_Page")

IndyTim / DataMan

---

