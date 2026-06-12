---
title: "Accessing External HD"
date: 2010-08-22
forum: General Help
---

### Post by docein on 2010-08-22
Hello everyone,

I am having issues copying files from an external HD originally from a Mac.
The HD is not recognized at all in my windows xp OS.
The HD is recognized and i can view most folders in ubunutu 10.04, (I hit a block when i go into users folder, but can bypass using gksu nautilus), however I am still unable to copy any documents, nor am I able to modify the permissions of any of the folders/files. 

When I attempt to edit a permission I get this message: 

Sorry, could not change the permissions of "100_0500.JPG": Error setting permissions: Read-only file system

and when I try to copy over straight from Ext. HD to Ubuntu:
The file "100_0500.JPG" cannot be handled because you do not have permissions to read it.

Here are some information from the terminal:


/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/doc/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=doc)
/dev/sdb2 on /media/5ec06976-85f3-3bdd-88fd-b43e131df2d9 type hfsplus (rw,nosuid,nodev,uhelper=udisks)



and also I have tried:


doc@doc-laptop:~$ sudo umount /dev/sdb2
[sudo] password for doc: 
doc@doc-laptop:~$ sudo fsck -r /dev/sdb2
fsck from util-linux-ng 2.17.2
fsck: fsck.hfsplus: not found
fsck: Error 2 while executing fsck.hfsplus for /dev/sdb2

and:
doc@doc-laptop:~$ sudo fsck -r /media/5ec06976-85f3-3bdd-88fd-b43e131df2d9
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Is a directory while trying to open /media/5ec06976-85f3-3bdd-88fd-b43e131df2d9

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


and also:
doc@doc-laptop:~$ sudo mount -o remount -o rw /dev/sdb2


The drive appears to have been either removed without properly being unmounted or some other type of damage. However, I am able to open up (using gksu nautilus) pictures and word documents and use the 'save as' command and save them onto my HD. They are locked, but I can set permissions like normal and then edit them as normal.


Any ideas? 

Thanks a ton in advance.

---

### Post by earthpigg on 2010-08-22
hi,

in gksu nautilus, try creating a second nautilus window *that is also root*, and copying the files there.

---

### Post by docein on 2010-08-22
Genius! Thank you very much! haha its the simple things that make it all worth while.

---

