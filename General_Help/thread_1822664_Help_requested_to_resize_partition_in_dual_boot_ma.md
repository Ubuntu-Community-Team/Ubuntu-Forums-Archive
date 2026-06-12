---
title: "Help requested to resize partition in dual boot machine..."
date: 2011-08-10
forum: General Help
---

### Post by mark111 on 2011-08-10
I am getting a message that I only have 1.2 GB remaining on my hard disk.  I know that this must be a partition problem, but I can't quite figure it out.  Some stats:

- dual boot Asus eeePC laptop with Ubuntu 10.04 (Lucid) and XP installed 
- hard drive of 150GB, made up of three partitions (according to GPARTED) 
   --sda1, an ntfs system with 144GB, of which 47GB is used
   --sda2, a FAT32 system with 4.9GB, of which 3.5GB is used
   --sda3, an unknown system with 39MB in it

The confusing part is that the file system (using properties for the highest directory for computer:/// shows 17.7GB used and 1.2GB free) is the bit that seems to relate to the notice of too little space.

If I use disk utility, there are two disks shown:  a 160GB hard disk which has more or less the same partitions as shown in gparted, and also separately a 31GB file called root.disk, and is at /dev/loop0.  I can speculate on this, but really have no idea...

I have access to all of the XP stuff under /host, and I keep all of my files under /host/several directories/my documents so that they are accessible under both XP and Ubuntu, though I rarely use the XP side of things.

What I would like to do is mount the partition that is not accessible and move my memory hogging files - mostly old data and emails - onto the newly mounted partition.  I haven't found this situation in the forums.  Can you help?

Cheers

---

### Post by mark111 on 2011-08-13
In the absence of a reply, I tried some other stuff.  Since the problem I was trying to solve was a message that my hard drive was out of space and I had plenty of room on it, I:

- deleted all of my old kernels using Synaptic package manager.  Searched for 2.6 (my kernels ran from 2.6.15 to 2.6.33), and deselected the ones other than the current and next most current.
- moved my email files from Thunderbird from /home/user to /host (which is the place where my XP files are located), and changed the source for those files in the Thunderbird settings.

Don't know which worked, but I am not getting those messages anymore.

---

### Post by sbraz on 2011-08-13
you can't resize mounted partitions, so you need to boot from somewhere else like an usb drive, or phisically move your hdd to another machine and do the job from there.

there are tons of correct ways to do that.
my way is by booting PartedMagic from an usb drive properly prepared using a program called "unetbootin". you can find it at ubuntu software center, or google. :)

---

### Post by Sef on 2011-08-13
Copy and paste this command:

```
sudo apt-get fdisk -l
```

That will show us the partitions that you have.

---

### Post by oldfred on 2011-08-13
From what you have indicated you do not have Linux partitions and if windows is in /host that means you have wubi.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

If you are using Ubuntu a lot, it may be time to convert:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

Resize wubi - bcbc
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

