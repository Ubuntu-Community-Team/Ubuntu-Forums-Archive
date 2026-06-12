---
title: "Folder Permissions -&gt; 2 hard disks"
date: 2006-04-20
forum: General Help
---

### Post by Jose Catre-Vandis on 2006-04-20
I get so far then ....

I have an Athlon 2200 with 2 x 160gb maxtors, Nvidia card etc
Am setting it up as a sole Ubuntu install
I think what I want is:
Mostly ext3 partitioning but with a small area of fat32 for windows sharing

My problems:

1. Ubuntu doesn't seem to automagically pick up on the 2nd hard drive, even though the partitioning took place during install. I was able to mount the drive through fstab.

My fdisk output:
```
Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14759   118551636   83  Linux
/dev/hda2           14760       14946     1502077+   5  Extended
/dev/hda5           14760       14946     1502046   82  Linux swap / Solaris

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14946   120053713+   5  Extended
/dev/hdb5               1       13631   109490944+  83  Linux
/dev/hdb6           13632       14946    10562706    b  W95 FAT32
```

Everything on hdb is logical in an extended partition

My fstab output:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc              /proc                proc    defaults        0       0
/dev/hda1       /                      ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none               swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy1  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy2  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy3  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy4  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy5  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy6  auto    rw,user,noauto  0       0

/dev/hdb5     /xmusic	          ext3	  defaults	       0	0
/dev/hdb6     /xwinsh		   vfat	    iocharset=utf8,umask=000	0	0
```

This all works nicely, apart from permissions on the linux mounts/folders. i am able to read and write to the xwinsh share, but have to be root to do anything on the linux mounts and folders, outside of /home

2. Permissions
This is driving me potty. I have been trying to think hard like Linux but the simplicity of XP keeps creeping back. The problem:

I get to something like above, but then I find that everything outside of /home is only writeable by root, making it difficult to instigate file copy operations. I did some work on umask in fstab and then chmodded 777 as root. I got somewhere, but on reboot the system would not boot to X or even give me a login. There seems to be plenty of advice here and on the wiki about sharing but not on local permissions. I have done plenty of googling and reading but nothing brings me close. Why cannot I not just copy files to folders I create (as user/root)? Should I build up a file structure in /home and share that? I want to share to other PC's on my LAN, and also use the box for http and ftp to the net. I want to do this as user rather than root, if possible. Having donw what the wiki said in terems of adding a second hard drive and mounting it (xmusic), I find I cannot copy/move files to it, and this is the same for any folder created in "/" using root.


Also, where have all my gigabytes gone? GParted is reporting only @ 115gb on my 160gb drives (this can't be the old 1000:1024 trick?)

](*,) ](*,)

---

### Post by Danimal666 on 2006-04-20
I'm having a similar problem. I've mounted my Windows (NTFS) partition in Ubuntu, but can't seem to make it writable. I set the umask to 000 in the fstab, but when I try to change the permissions with chmod, it refuses, on the grounds that it's a read only filesystem. I'm the only one who uses this computer, it's not on a LAN, and I don't let people I don't trust use it, so my security standard isn't exactly paranoiac. I just want to be able to read and write and execute freely like I could in XP.

---

### Post by Jose Catre-Vandis on 2006-04-20
[QUOTE=Danimal666]I'm having a similar problem. I've mounted my Windows (NTFS) partition in Ubuntu, but can't seem to make it writable. I set the umask to 000 in the fstab, but when I try to change the permissions with chmod, it refuses, on the grounds that it's a read only filesystem. I'm the only one who uses this computer, it's not on a LAN, and I don't let people I don't trust use it, so my security standard isn't exactly paranoiac. I just want to be able to read and write and execute freely like I could in XP.[/QUOTE]

Not recommended to try to WRITE to ntfs partitions (although it can be done), check out the wiki for further info, or the unofficial guide. Syntax for ntfs partition in fstab goes something like this, but this is only readable:

```
/dev/hda7       /media/VIDEO  ntfs    nls=utf8,umask=0222 0       0
```

Best to create a FAT 32 area to share with your Windows setup

---

### Post by Danimal666 on 2006-04-20
Not even an option. I'm quite sure NTFS can't be converted to FAT32, which is for the birds anyway. I'd sooner just copy the data in question to my Linux partition, and that's what it looks like I'm gonna have to do.

---

### Post by Jose Catre-Vandis on 2006-04-20
Looks like hard work but try here:

[http://www.ubuntuforums.org/showthread.php?t=142481&highlight=folder+permissions](http://www.ubuntuforums.org/showthread.php?t=142481&highlight=folder+permissions)

Anyhow, we have shifted off topic, back to my enquiry :-)

---

