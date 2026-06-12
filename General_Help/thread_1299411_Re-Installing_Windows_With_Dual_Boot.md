---
title: "Re-Installing Windows With Dual Boot"
date: 2009-10-23
forum: General Help
---

### Post by Majorflam on 2009-10-23
I have Ubuntu installed on a laptop that originally came with Windows Vista. After installing Ubuntu I now have a dual boot setup.

If I re-install Windows using the recovery method that is on the hard drive, will this affect my Ubuntu installation? Will the Vista reinstaller recognise the Ubuntu section of my hard drive?

TIA

---

### Post by phillw on 2009-10-23
Possibly along these lines ?

[http://ubuntuforums.org/showthread.php?t=863467](http://ubuntuforums.org/showthread.php?t=863467)

Hope that helps.

By the way - before you try anything..... BACKUP your stuff !!!!

[http://ubuntuforums.org/showthread.php?t=35087&highlight=backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup)

Regards,

Phill.

---

### Post by Majorflam on 2009-10-23
That's excellent. I have the recovery partition and also the CD's that I made.

Rather than re-install Vista, I'd actually be happy to get rid of it and free up all the disk space... basically make the current Vista partition a storage partition. I'd always have the option of re-installing Vista if I really wanted to.

How would I go about deleting the partition that houses Vista, and formatting it completely so that I have the space freed up?

---

### Post by mr_steve on 2009-10-23
Checkout [GParted]("http://gparted.sourceforge.net"). They have a bootable CD you can use to resize and reformat partitions non-destructively. I'd still backup first anyway, although I've never had a problem.

Also, if you ever do use your recovery partition or discs, be careful. Some recovery tools will just cheerfully wipe the entire drive before restoring the factory image.

---

### Post by Majorflam on 2009-10-24
Is it possible to use a GUI of Gparted from Ubuntu if I'm not changing the partition that ubuntu is installed on?

---

### Post by mr_steve on 2009-10-24
Yes, you can install Gparted on Ubuntu and use it to format other partitions. You would only need the LiveCD if you wanted to resize any partitions, like deleting the Windows partition and growing the Ubuntu partition to fill the space.

---

### Post by blwizard on 2009-10-24
> **Majorflam said:**
> That's excellent. I have the recovery partition and also the CD's that I made.

Rather than re-install Vista, I'd actually be happy to get rid of it and free up all the disk space... basically make the current Vista partition a storage partition. I'd always have the option of re-installing Vista if I really wanted to.

How would I go about deleting the partition that houses Vista, and formatting it completely so that I have the space freed up?

It's easy, just a few commands away.

Make sure you know which partition vista resides on, say it's /dev/sda4. In ubuntu terminal, invoke 
```
sudo mkfs.ext3 /dev/sda4 
```
(or whatever partition format you want, just type mkfs and press tab and all the options you have will show up). Then that partition is ready for use under your ubuntu. Just mount that partition and store whatever you want to on it.

You may want to put an entry for that partition in /etc/fstab to auto-mount that partition on system start.

---

### Post by Majorflam on 2009-10-24
A clean format of the windows partition would suit me, as I probably won't be mounting it every session anyway. In that case, I'll just load Gparted in Ubuntu and format the windows partition from the GUI.

Many thanks for all your help, guys. I really appreciate it.

---

