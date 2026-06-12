---
title: "Removing  mount point from thumb drive"
date: 2010-07-05
forum: General Help
---

### Post by Silvernail on 2010-07-05
When I insert this USB drive, a 'ls' shows this:
> 
dave@dave:/media/$ ls
90B9-56FA  cdrom  cdrom0  Teragb  U3 System

I can remover 90B9-56FA but not 'U3 System'
> 
dave@dave:/media$ ls "U3 System"
autorun.inf  LaunchPad.zip  LaunchU3.exe> 
dave@dave:/media$ ls -l "U3 System"
total 5536
-r-------- 1 dave dave     277 2007-02-12 13:53 autorun.inf
-r-------- 1 dave dave 4558081 2007-02-12 20:23 LaunchPad.zip
-r-------- 1 dave dave 1110016 2007-02-12 19:33 LaunchU3.exe> 
dave@dave:/media$ ls
90B9-56FA  cdrom  cdrom0  Teragb  U3 System> 
dave@dave:/media$ cd "U3 System"> 
dave@dave:/media/U3 System$ sudo rm *
rm: cannot remove `autorun.inf': Read-only file system
rm: cannot remove `LaunchPad.zip': Read-only file system
rm: cannot remove `LaunchU3.exe': Read-only file system

> dave@dave:/media/U3 System$ chmod 777 *
chmod: changing permissions of `autorun.inf': Read-only file system
chmod: changing permissions of `LaunchPad.zip': Read-only file system
chmod: changing permissions of `LaunchU3.exe': Read-only file system

Here is the tail end of 'mount'> 
dave@dave:/media/U3 System$ mount
/dev/sdb1 on /media/Teragb type ext3 (rw,nosuid,nodev,uhelper=udisks)
/dev/sr1 on /media/U3 System type iso9660 (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdc1 on /media/90B9-56FA type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

I have nothing on the drive worth saving. Would a:
> fdisk /media/90B9-56FA remove it with out damage or would 1 of these listed in the 'fdisk manual' be more apropos?
```
cfdisk(8), sfdisk(8), mkfs(8), parted(8), partprobe(8), kpartx(8)
```

Thanks for any help or insight you might have in matter.

---

### Post by Silvernail on 2010-07-08
Information and solution here:
[http://www.linuxquestions.org/questions/linux-hardware-18/removal-of-u3-crap-from-usb-flash-how-410539/page2.html](http://www.linuxquestions.org/questions/linux-hardware-18/removal-of-u3-crap-from-usb-flash-how-410539/page2.html)

---

