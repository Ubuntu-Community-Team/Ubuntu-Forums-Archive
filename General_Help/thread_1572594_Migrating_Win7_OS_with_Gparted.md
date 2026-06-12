---
title: "Migrating Win7 OS with Gparted?"
date: 2010-09-11
forum: General Help
---

### Post by Tango91 on 2010-09-11
Hey Guys,

I currently run Ubuntu 10.04 on my laptop and i'm looking to get it on my big desktop rig as well.

My desktop PC has 2 hard drives, a 160Gb drive which currently has Windows XP, and an 80Gb drive with WIndows 7 on it.

I'd like to wipe the XP drive, move the Windows 7 install across, and install Ubuntu on the 80Gb drive.

Is this possible with Gparted or via the console while running a livecd session?

Any tips would be appreciated, thanks in advance,

Tango91 :)

---

### Post by coffeecat on 2010-09-11
In theory you could use Gparted because (I believe) it uses dd to copy partitions which is way of copying the raw data on the drive. In practice I wouldn't risk it - I would prefer to use a Windows tool to move/copy a Windows partition. There is a proprietary, but free, app that does a similar job to Norton Ghost or Acronis True Image. Here:

[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

I've successfully used this to copy a Windows 7 (RC) installation from one hard drive to another. First you make an image onto an external medium and then you restore from the image onto the target partition. The main limitation is that the destination partition must be at least as big as the original one. One nice thing about Macrium is that to make the restore you boot up with a Linux based CD (which you prepare from Macrium in Windows). I enjoy the irony.

Another option would be to use clonezilla, but I have no direct experience of this.

---

### Post by Mark Phelps on 2010-09-11
Listen to what coffeecat is telling you ... use MS Windows tools to migrate MS Windows OS partitions; use Linux tools to do the same with Linux OS partitions.

---

### Post by srs5694 on 2010-09-11
Windows is very very fussy about its boot partition, and Linux-based NTFS-copying tools don't take care to change the things that need to be changed to keep Windows bootable when you copy an NTFS partition from one location or drive to another. If you're very lucky it might work, but if not it won't, and you'll have a very hard time fixing it. (In fact, I've never succeeded myself after such issues; I've always just re-installed from scratch.)

---

### Post by wilee-nilee on 2010-09-11
The only thing I would add here is that on the desktop with 2 HD and XP and W7 that you check with the bootscript in my signature what the boot setup is. It may be that your boot on that desktop is in XP, especially if you installed W7 second and you have a MS bootloader to choose either XP or W7.

---

