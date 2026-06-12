---
title: "Ubuntu won't let me boot Windows 7 disk at start up?"
date: 2011-08-08
forum: General Help
---

### Post by rbkhockey83 on 2011-08-08
Hi guys, I have ubuntu on 2 computers, one is an older laptop and it's Ubuntu 8.04.  I finally resolved a Grub 15 error... but now I want to install Windows 7 on that computer.  So I turn the computer on and press f12, then select "Boot from CD-Rom" but then Ubuntu still goes on to boot up.  And yes the Windows 7 CD is in the disk tray.  Any help?

Thanks,
Sean

---

### Post by Sotanaht on 2011-08-08
Try the disk on a different computer to see if there's something wrong with the disc itself

---

### Post by rbkhockey83 on 2011-08-08
Ok, I tried that and the disc worked (It was on an XP Machine, not Ubuntu).  So it's definitely the computer or the Ubuntu OS.

---

### Post by Basher101 on 2011-08-08
Try changing boot order in the BIOS. Did you free up some space for windows? you will need a NTFS filesystem. Also windwos partitions must be always primary. When you isntall windows after ubuntu, your GRUB will get deleted and you will have to reinstall it again using a live cd of ubuntu. There are threads how to restore it, just search

---

### Post by deserthowler on 2011-08-08
> **rbkhockey83 said:**
> So I turn the computer on and press f12, then select "Boot from CD-Rom" but then Ubuntu still goes on to boot up.  And yes the Windows 7 CD is in the disk tray.

This sounds like a BIOS setting or hardware problem.  If the BIOS and the CDROM work, the BIOS should not take you to UBUNTU until it decides it can't do anything with the CDROM.

Earl

---

### Post by StrangeWill on 2011-08-08
> **deserthowler said:**
> This sounds like a BIOS setting or hardware problem.  If the BIOS and the CDROM work, the BIOS should not take you to UBUNTU until it decides it can't do anything with the CDROM.

Earl

Probably this, every time I've had this issue the DVDROM was garbage or the DVD was trashed.


Also, you're not putting a Windows 7 *DVD* in a CDROM are you? I've done that before, heh.

---

### Post by rbkhockey83 on 2011-08-08
My BIOS is set to boot from the CD-Rom, and I know the drive works because I installed the ubuntu off of a CD (It's an 8.04 CD Ubuntu mailed me in like '08. lol).  Which leads me to believe I'm putting a DVD in a CD drive=D>, but the drive doesn't say what it is on the tray.  The disc is a DVD-R though (Not that it's a bootleg copy or anything..:-$) .  Hahah I feel smart...

---

### Post by fdrake on 2011-08-08
> **rbkhockey83 said:**
> My BIOS is set to boot from the CD-Rom, and I know the drive works because I installed the ubuntu off of a CD (It's an 8.04 CD Ubuntu mailed me in like '08. lol).  Which leads me to believe I'm putting a DVD in a CD drive=D>, but the drive doesn't say what it is on the tray.  The disc is a DVD-R though (Not that it's a bootleg copy or anything..:-$) .  Hahah I feel smart...

it reminded me of when i thought changing drivers or software on windows would make my cd-rom play my first dvd movies... an entire weekend lost in nothing .. . .  

I perfectly know how you feel. lol

---

