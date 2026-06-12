---
title: "The disk drive for /media/sdb1 is not ready yet or not present"
date: 2011-01-25
forum: General Help
---

### Post by 013raptor on 2011-01-25
During the boot, the following message appears:[INDENT]**The disk drive for /media/sdb1 is not ready yet or not present**
**Continue to wait, press S to skip or M for manual recovery.**

[/INDENT]This started to appear after I use the "pysdm" application.
I already searched the forum and nothing worked for me.

---

### Post by khamil8686 on 2011-01-25
pysdm or psydm looks like it might have incorrectly configured your fstab file, go here
[https://help.ubuntu.com/community/InstallingANewHardDrive]("https://help.ubuntu.com/community/InstallingANewHardDrive")
and scroll down to the part about Mount The Drive > Automatic Mount at boot, hopefully this helps! :)

---

### Post by 013raptor on 2011-01-25
I tried to add this:[INDENT]/dev/sdb1    /media/sdb1   ext3    defaults     0        2
[/INDENT]but did'nt worked.

Before that my fstarb was like this:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda5 :
UUID=bddc6418-653d-490c-bddb-1f5d38d335d5    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda1 :
UUID=D0C0EEADC0EE994C    /media/Windows    ntfs    defaults,nls=utf8,umask=0222    0    0
#Entry for /dev/sda6 :
UUID=1e6767cc-0615-443d-b124-31081410e45a    none    swap    sw    0    0
/dev/fd0    /media/floppy0    auto    rw,user,noauto,exec,utf8    0    0
#Entry for /dev/sdb1 :
UUID=40B2-75B0    /media/sdb1    vfat    defaults    0    0



---

### Post by 013raptor on 2011-01-25
I edited the last line and leave it like this:

[INDENT]UUID=40B2-75B0   /media/sdb1   vfat   defaults[COLOR=red],noauto[/COLOR]  0   0

[/INDENT]Now the problem is gone. :p

---

### Post by khamil8686 on 2011-01-25
change your fstab back to how it was before

> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc nodev,noexec,nosuid 0 0
#Entry for /dev/sda5 :
UUID=bddc6418-653d-490c-bddb-1f5d38d335d5 / ext4 errors=remount-ro 0 1
#Entry for /dev/sda1 :
UUID=D0C0EEADC0EE994C /media/Windows ntfs defaults,nls=utf8,umask=0222 0 0
#Entry for /dev/sda6 :
UUID=1e6767cc-0615-443d-b124-31081410e45a none swap sw 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
#Entry for /dev/sdb1 :
UUID=40B2-75B0 /media/sdb1 vfat defaults 0 0

the UUID for the /dev/sdb1 entry looks very short compared to ones ive seen before, possibly it is wrong?
find the uuid of /dev/sdb1 by entering this in terminal
```
blkid /dev/sdb1
```

that will give you the UUID, replace the
UUID=40B2-75B0 /media/sdb1 vfat defaults 0 0 
with 
UUID=*UUID returned by blkid* /media/sdb1 vfat defaults 0 0

you can also try to change the /media/sdb1 field to be / so that your main drive gets mounted as root instead of /media/sdb1

---

