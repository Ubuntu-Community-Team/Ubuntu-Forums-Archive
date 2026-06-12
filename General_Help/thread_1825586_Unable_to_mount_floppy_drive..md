---
title: "Unable to mount floppy drive."
date: 2011-08-15
forum: General Help
---

### Post by Abydosgater on 2011-08-15
I am working on an old PC and I am trying to mount a floppy disk.
The disk is formatted as Fat12 with > mkdosfs -F 12 /dev/fd0

Weather it auto mounts or I mount it with sudo mount > /dev/fd0 /media/floppy0 it says it works fine, but if I add files to it,remove the disk and put it in another machine nothing is on the disk. 

The files I add to the disk just get added to /media/floppy0 as a normal directory.
If I try to umount /dev/fd0 it says the device is not mounted, even directly after I mount it.

Has anyone any ideas why it may not mount?

Thanks for your time in reading.
Andy

---

### Post by kr651129 on 2011-08-15
Are you moving files to it via command line or with the GUI...any reason you aren't using a thumb drive?

---

### Post by Abydosgater on 2011-08-15
The files are moved by command line / shell script.

Im working on a bootdisk and must be fat12 floppy. The bootloader writes perfectly fine to the reserved sector (bootsector) but with the problems mentioned above.

---

### Post by smurphy_it on 2011-08-15
Are you able to write any files on that disk (or another) on this machine, and have it readable by the other machine ?

If you can copy/move files to it from Machine A (using different floppies for a test) and are unable to read them on MachineB, I'd suspect a hardware issue with your floppy drive.

---

### Post by Abydosgater on 2011-08-15
I dont think its a hardware problem with the floppy drive for the following reasons:

1. I can DD my bootloader to the first sector and boot from it just fine.
2. My bootloader can read and traverses the FAT as an empty table.
3. If I fsck /dev/fd0 it tells me that the filesystem has 2 files.

So other software can use the drive just fine. But xbuntu will not mount the drive. I mount it and the mount command shows no error. I write files to the mounted directory (Ive tried the default xbuntu /media/floppy0 and I have tried mounting to /mnt/floppy, both exist). The files are written to the directory as a standard folder.. and are not actually written to the device.

Andy

UPDATE: After a bit more searching I found the udisks command. If I use > udisks --mount /dev/fd0
udisks --unmount /dev/fd0
The file system mounts and works perfectly like expected. Is there any way I can get this to happen automatically. Its already in the fstab but that results in the initial problem.

---

### Post by smurphy_it on 2011-08-16
glad to hear it's not hardware.  The floppy drive can sometimes go out of alignment slightly.  It won't stop you from reading/writing to floppy disks on your machine, but other machines won't be able to read them, because they were written out-of-alignment.

---

### Post by kr651129 on 2011-08-16
Please post your /etc/fstab

it should say look like this

```
/dev/fd0 /media/floppy0 vfat rw,user,noauto 0 0

```

If it doesn't then change it to this, reboot and try it again

---

### Post by johnalexrob on 2011-09-11
A friend of mine is having this same problem on an installation of Natty I did for him. It won't mount, automatically or manually. The gui disk utility recognises the drive but says there is no media inserted, and fdisk says that the partition table has a problem. I did not try the udisks command though. I have checked to see if it was created as sdc, but I could not tell. I've gone through everything I know how to do and I came up with nothing. I read another post about something similar, but it was of no help. Any ideas?

---

