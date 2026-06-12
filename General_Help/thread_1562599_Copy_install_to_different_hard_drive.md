---
title: "Copy install to different hard drive"
date: 2010-08-27
forum: General Help
---

### Post by primetime34 on 2010-08-27
I want to copy my current install of Ubuntu 10.04 from one hard drive to another which will run on the same computer it is on now.  What is the best way to do this?

---

### Post by an0dos on 2010-08-27
> **primetime34 said:**
> I want to copy my current install of Ubuntu 10.04 from one hard drive to another which will run on the same computer it is on now.  What is the best way to do this?

Check out clonezilla live. It is a live cd that can do what you need.

Note: clonezilla will only work if the new hard drive is the same size or larger than your current one.

---

### Post by cj.surrusco on 2010-08-27
You can use a GParted disk to copy the partition(s) over to another hard drive, then all you would need to do is reinstall the bootloader.

---

### Post by primetime34 on 2010-08-27
I need to reinstall bootloader.  How do I do that?  Can I use original hard drive install to install boot loader on new hard drive (they are both external hard drives), or do I have to use a live cd?

---

### Post by finny388 on 2010-08-27
I found **[Partimage]("http://www.partimage.org/Main_Page")** way easier to use than Clonezilla.

It is found on **[SystemRescueCD]("http://www.sysresccd.org/")**.

Boot from a usb key (or cd) and at the prompt type **partimage**.

This starts the program. It will copy the complete image.

The only trick is I believe you have to mount the drives manually at the prompt before launching partimage.

---

### Post by cj.surrusco on 2010-08-27
> **primetime34 said:**
> I need to reinstall bootloader.  How do I do that?  Can I use original hard drive install to install boot loader on new hard drive (they are both external hard drives), or do I have to use a live cd?

You need the live CD. Check out section 13 [here]("http://ubuntuforums.org/showthread.php?t=1195275").

---

### Post by primetime34 on 2010-08-28
Partimage won't work because I'm using ext4 and it doesn't support that.

Clonezilla isn't working for me....it doesn't create a recognizable file system on the new hard drive.  Looking at in gparted just says it is an unknown file system (my current system is ext4)

I'm looking at using the gparted live cd next.  Don't know how that'll turn out...

---

### Post by primetime34 on 2010-08-28
I'm having little success....any other guidance/help?  Thanks.

---

### Post by cj.surrusco on 2010-08-28
Try using the Ubuntu live CD. I can't remember if it has Gparted on it by default, but if it doesn't, you can just install it. Just open up Gparted and copy your Ubuntu partition, and any swap partitions to the new hard drive. Then follow the steps to reinstall the bootloader from my last post.

---

### Post by C.S.Cameron on 2010-08-28
Boot Live CD and use ```
dd if=/dev/sda of=/dev/sdb
``` it will clone sda to sdb, sdb will be bootable if sda was.
sdb must be as big or bigger than sda.
Process takes some time.

For more info see:

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

### Post by donthem on 2010-08-28
If you use the alternative live cd you can choose rescue and it will allow you to reinstall the grub to a desired drive.  This is probably in the regular live cd but I have not used it in a while

gl

---

### Post by primetime34 on 2010-08-28
> **C.S.Cameron said:**
> Boot Live CD and use ```
dd if=/dev/sda of=/dev/sdb
``` it will clone sda to sdb, sdb will be bootable if sda was.
sdb must be as big or bigger than sda.
Process takes some time.

For more info see:

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)


You aren't kidding about taking a lot time.  I'm 3 hours in and it's still not finished. :D

---

### Post by C.S.Cameron on 2010-08-29
They could at least provided some blinking lights or something to let you know it is working.
You just got to have faith.

---

### Post by primetime34 on 2010-08-30
> **C.S.Cameron said:**
> They could at least provided some blinking lights or something to let you know it is working.
You just got to have faith.

Took 7 hours....worked great!!  Thanks.

---

