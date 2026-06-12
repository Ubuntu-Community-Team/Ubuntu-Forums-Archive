---
title: "Grub &amp; Partitions"
date: 2006-03-31
forum: General Help
---

### Post by AndyOB on 2006-03-31
Hi,
Attached is a XP shot of my disk layout (2 SATA drives). I am trying to install Ubuntu on a completely separate disk to WinXP, and swap whichever one boots by swapping the BIOS settings of which is Sata1 and Sata0, which is easy enough. I am a little confused about where to put Grub though. I don't really want to put it in the MBR of my XP disk, so where do I put it? Is there an MBR for the 2nd disk? How do I reference this during the install?

---

### Post by DoorGunner on 2006-03-31
Something you can try is to physically move your drives so that XP is on drive 2 vice drive 1. 

Install Grub on the new disc 1 mbr....that way you can preserve the origional windows mbr.

This is how my grub config looks for windows. 

title=Windows XP Home Editions SP2
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,1)
makeactive
chainloader +1

windows tends to want to be installed on the first drive.....however the map configuration will fake it out to think that it is....make sence?

---

### Post by AndyOB on 2006-04-01
[QUOTE=DoorGunner]Something you can try is to physically move your drives so that XP is on drive 2 vice drive 1. [/QUOTE]

This is essentially the same thing as swapping around the assignment of the SATA ports. So if I put "drive1" as my ubuntu drive with xp as "drive 2", then will the installer for GRUB only put itself onto the ubuntu drive, even if it detects that xp is on the other disk?

---

### Post by DoorGunner on 2006-04-01
yes ....it wont detect the mbr of the xp.....

Another way to do it is to tell your bios to start with disk 2..... however, i havent tried that one....it should work the same....

The end result is the same....to preserve windows MBR which can be a bitch to recover. and yes with the mapping portion XP will be detected and function.....

XP prefers to be on Drive one .... however the map will remap it so it is drive one..... It happens transparently to you....

---

### Post by Sutekh on 2006-04-01
[QUOTE=AndyOB]Hi,
Attached is a XP shot of my disk layout (2 SATA drives). I am trying to install Ubuntu on a completely separate disk to WinXP, and swap whichever one boots by swapping the BIOS settings of which is Sata1 and Sata0, which is easy enough. I am a little confused about where to put Grub though. I don't really want to put it in the MBR of my XP disk, so where do I put it? Is there an MBR for the 2nd disk? How do I reference this during the install?[/QUOTE]Yes there is a way to do this.  When you asked the location to install GRUB you can choose exactly where you want it to go.

All you need to do is make note of the device location (/dev/) of the SATA disc that Windows and Ubuntu are on.

For example if Windows is installed on /dev/sda1 and you then install Ubuntu on /dev/sdb1, then when GRUB asks where it should be installed, enter ```
/dev/sdb1
```

Then you will have an intact Windows MBR on /dev/sda1 and a working GRUB on /dev/sdb1.  

GRUB will detect the Windows XP installation and add it to the boot options.  

You will want and need the disc with Ubuntu to be your priority boot drive in BIOS so GRUB starts, when your PC boots.  If the Windows disc boots first then you won't get to the GRUB menu and boot options.  Because GRUB can boot both Ubuntu and Windows there will be no need to continuously change the boot order.

---

### Post by AndyOB on 2006-04-03
For some reason Grub doesn't like being pointed to another drive  (ie. /sdb1). what I ended up doing was configuring my SATA drives as IDE drives via the BIOS. This allowed me to get the Master/Slave equivalent and then it just treated my Ubuntu drive as the boot drive and GRUB installed to the MBR no problems, with the option of booting into XP too :)

---

