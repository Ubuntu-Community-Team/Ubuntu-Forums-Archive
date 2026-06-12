---
title: "Ubuntu 9.04 and Acronis True Image"
date: 2010-04-02
forum: General Help
---

### Post by linuxbox25 on 2010-04-02
Hello there! i'm a new Ubuntu user and i love it thus far but i am in need of figuring out which version of Acronis True Image I can use for backing up my system and whatnot.
what version of True Image can i use with Ubuntu and has anyone gotten it to work with Ubuntu 9.04?  perhaps i should use the latest 9.10 Ubuntu instead but i was hoping to talk to someone who has successfully installed Acronis True Image on a recent version of Ubuntu and maybe have some instruction on what needs to be done to make it work!  Thanks for any information you can give me!

---

### Post by Pjotr123 on 2010-04-02
> **linuxbox25 said:**
> Hello there! i'm a new Ubuntu user and i love it thus far but i am in need of figuring out which version of Acronis True Image I can use for backing up my system and whatnot.
what version of True Image can i use with Ubuntu and has anyone gotten it to work with Ubuntu 9.04?  perhaps i should use the latest 9.10 Ubuntu instead but i was hoping to talk to someone who has successfully installed Acronis True Image on a recent version of Ubuntu and maybe have some instruction on what needs to be done to make it work!  Thanks for any information you can give me!

Acronis True Image (which I love!) isn't available for Linux, at least not as desktop application. However, you can use the Acronis True Image Rescue CD both for creating and for restoring images. That's what I do, myself. The Rescue CD is a LiveCD and operating system independent.

The only thing I used Acronis TI in Windows for, was to create such a Rescue CD (you can choose that option within Acronis TI for Windows).... Then you can simply boot your computer from the Rescue CD and use it to backup and restore your Linux and Windows partitions.

---

### Post by lindsay7 on 2010-04-02
I use the True Image install disk to do the backup and restore.  I did not create a special disk.  After all if your system crashes you are going to lose the True Image program on your hard drive so the install disk has to be used to do a restore.  I have found that any thing that is on you drive will be backed up regardless of what file system you use, i.e. fat, ext3, ext 7. or ntfs.

---

### Post by howefield on 2010-04-02
Ubuntu 9.04 by default uses an inode size of 256 bytes instead of the previous 128 byte standard which True Image will back up in sector-by-sector mode. It will work, but the backup file could be huge.

Clonezilla might be a better bet.

---

### Post by linuxbox25 on 2010-04-02
well my system hasn't crashed and yea i think they have true image echo server or something that is for linux.  they have a linux agent that you can install on a linux machine and connect to it from a windows based pc and you can use that to backup your linux system...LIVE.  that's the thing.  i need to backup the system live because i can't shut it down.  it's being used as a web server and whatnot and i need to image the partition and everything LIVE in real time.  was wondering if anyone had any luck installing the linux agent that allows one to connect to it from a windows pc and do the backup.

---

### Post by Mark Phelps on 2010-04-02
Two things about Acronis True Image ...

First, while it may have worked on Ext3 filesystems, I tried it on a new install of 9.10, and it barfed on the Ext4 filesystem.  So, my guess is that it does NOT support Ext4 filesystems.  However, that said, I never really tried it on 9.04, so I don't know if it works with Ext3 filesystems.  What I read in their forums is that is can read SOME Linux filesystems, but it has to write the image to an MS Windows filesystem.

Second, Acronis is currently conducting a beta testing cycle for Acronis True Image for Linux.  So, they could very well have a working product out any time now.

Since I, too, have to back up 9.10 partitions, I've found that Clonezilla is an excellent solution.

---

### Post by agamotto on 2010-04-02
I use the Acronis True Image cd to do an 'image' or clone of my system drive.  No matter what filesystem you use, it will bitcopy the whole disk.  An average backup for me takes only 30minutes.  I do this bi-weekly, and it is all working out for me.  I might try Clonezilla, as I had not heard of it before I had started using True Image.

---

### Post by linuxbox25 on 2010-04-02
yea but no solution for working in a live environment?  some can't shut down to backup a system.

---

### Post by howefield on 2010-04-03
> **linuxbox25 said:**
> but no solution for working in a live environment?

[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)

---

### Post by linuxbox25 on 2010-04-09
could i use norton ghost?  i've heard it's faster than clonezilla.  does ghost have a bootable cd process that would clone my running linux O.S.?

---

