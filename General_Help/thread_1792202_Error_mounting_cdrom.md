---
title: "Error mounting cdrom"
date: 2011-06-27
forum: General Help
---

### Post by warri0r on 2011-06-27
Whenever i insert a cd and click on the drive icon, the window just hungs up. later the following error pops up

```
Error mounting CDNAME
DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending
```

i have no issues in mounting/unmounting usbsticks.

i m clueless, plz throw some light over this. thanks

---

### Post by nzjethro on 2011-06-27
[This thread]("http://ubuntuforums.org/showthread.php?t=1175638") appears to have a number of possible solutions, ranging from a CLI:

```
sudo rm /media/.hal-mtab
```

to a Graphical solution with Gparted. Please try these, and post back with any progress.

---

### Post by warri0r on 2011-06-28
Tried those solution already,

i removed auto-mount from nautilus config but i dont think it would work for cdroms

when i tried to execute the following cmd, its just kept processing

sudo mount /dev/cdrom /media/folder

I can see the CD label name over the drive but when i click on the drive icon, it just wont show the files but hungs up.

plz help, thanks


P.s I checked my cdrom by accessing it from live cd and its working fine. So there is no problem with hardware

---

### Post by warri0r on 2011-06-28
My configuration info, hope this helps
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.10
Release:	10.10
Codename:	maverick

uname -a
Linux compname 2.6.38-02063808-generic #201106040910 SMP Sat Jun 4 10:51:30 UTC 2011 i686 GNU/Linux

---

### Post by nzjethro on 2011-06-28
Please post the output of

```
sudo fdisk -l
```

---

### Post by warri0r on 2011-06-28
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x90000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          24      192748+  de  Dell Utility
/dev/sda2              25        1983    15728640    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3   *        1983        7584    44995584   83  Linux
/dev/sda4            7585       37712   242003129+   5  Extended
/dev/sda5            7585        8331     6000246   82  Linux swap / Solaris
/dev/sda6            8332       37712   236002851   83  Linux

```

---

### Post by warri0r on 2011-07-01
** bump **

Any help? :(

---

### Post by matthewls on 2011-07-01
I had exactly the same problem, but solved it by upgrading to kernel 2.6.39.2. What a relief!

But, to upgrade to the kernel, I also had to upgrade to[SIZE=1] [/SIZE]                                                                            **[SIZE=1]module-init-tools 3.13-1ubuntu[/SIZE]**

Otherwise, the image would not install.

Hope it works for you too.

Cheers,
Matthew

---

### Post by warri0r on 2011-07-04
@matthewls nah, this is a development machine. I cant risk upgrading a kernel as i m not sure its highly stable.

Is ther any other solution for this? my cdrom is completely inaccessible :(

thanks

---

### Post by warri0r on 2011-07-06
** Bump **

---

### Post by warri0r on 2011-07-10
** Bump **

No help ? :(

---

