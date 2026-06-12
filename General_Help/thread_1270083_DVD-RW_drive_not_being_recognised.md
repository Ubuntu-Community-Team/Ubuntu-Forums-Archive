---
title: "DVD-RW drive not being recognised"
date: 2009-09-19
forum: General Help
---

### Post by jclmusic on 2009-09-19
Yesterday, I put a new internal DVD writer drive in my computer. It doesn't seem to be recognised by Ubuntu. I checked the internal cables and everything. 

I am running Ubuntu 9.04 (Jaunty). Do I need to edit fstab? If so, how do I find out the UID?

---

### Post by plucky on 2009-09-19
> **jclmusic said:**
> Yesterday, I put a new internal DVD writer drive in my computer. It doesn't seem to be recognised by Ubuntu. I checked the internal cables and everything. 

I am running Ubuntu 9.04 (Jaunty). Do I need to edit fstab? If so, how do I find out the UID?

Post the contents of your **/etc/fstab** file.

Is this a replacement for another CD/DVD drive?
Can you boot from the drive?
Can you see the drive in the BIOS window?
How are you trying to access the drive?

My fstab file has this ```
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
``` line for my DVD-RW drive.

Good luck

---

### Post by jclmusic on 2009-09-19
Here's the contents of my fstab file:
```

# /etc/fstab: static file system information.
#
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=150ce765-b83c-458f-839d-7bf1460080bd /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=67a650e2-4b51-4a02-9e14-bf601c0a1ba3 /home           ext3    relatime        0       2
# /music was on /dev/sdb1 during installation
UUID=48EF-976B  /music          vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda2 during installation
UUID=3720b43a-0d9b-425c-ab54-c3c2b591df8b none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=97d8742f-8fb2-49d8-a35d-14261a876135 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

I have 2 cd/dvd drives in there. 1 stopped working recently (drive would not open, same on miltiple OS's), so I replaced it with this new one. /media/cdrom0 is the other drive. The one that broke was /media/cdrom1, but it has gone from fstab. Hence why I thought I might need to add a new line.

I am trying to access the drive by putting a CD in there and, when it doesn't pop up on the desktop, trying to manually mount it. 

I will now reboot and see if I can boot from the drive or see it in the BIOS screen.
EDIT: Yes to both.

---

### Post by plucky on 2009-09-20
> /dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


Should that be ```
/dev/[color=red]scd0[/color]       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

and if you have two drives the second should be ```

/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

```

Are the drives Sata or Pata?
Are you using cable select or Master/slave?


Good Luck

---

