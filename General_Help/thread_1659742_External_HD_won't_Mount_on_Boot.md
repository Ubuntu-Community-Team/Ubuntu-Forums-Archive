---
title: "External HD won't Mount on Boot"
date: 2011-01-04
forum: General Help
---

### Post by CrimsoniteX on 2011-01-04
Hi guys,

I need a hand with mounting an external hd on boot with ubuntu server. I am aware of modifying the fstab, but that doesn't seem to be working. Here is an output:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/SERVER-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=6f21f0a8-1745-4d02-b88b-11e71f656089 /boot           ext2    defaults        0       2
/dev/mapper/SERVER-swap_1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0
/dev/sbd1 /media/externalHD auto auto,user,rw,exec,nobootwait 0 0
```

The problem is with the last line. Once booted into the server, I can mount using the following command:

```
sudo mount -t ntfs-3g /dev/sdb1 /media/externalHD
```

I know I can work around it by running a script with the previous command at startup, however I think I am simply doing something wrong. Is there a better way?

Any help would be greatly appreciated!

---

### Post by cariboo on 2011-01-04
You need to put the file system type in the last line of your /etc/fstab, instead of auto.

---

### Post by CrimsoniteX on 2011-01-04
Thanks for the response. 
I tried the following and none worked:
```
/dev/sbd1 /media/externalHD auto ntfs-3g,user,rw,exec,nobootwait 0 0
```
```
/dev/sbd1 /media/externalHD ntfs-3g auto,user,rw,exec,nobootwait 0 0
```
```
/dev/sbd1 /media/externalHD ntfs-3g,user,rw,exec,nobootwait 0 0
```

I tried it without the nobootwait tag as well, and it hung on bootup.

---

### Post by seawolf167 on 2011-01-04
Take a look at the link to fstab in my sig (its suggested to use UUIDs instead of the partition label especially for external hdds).

A program to add a fstab for a ntfs volume is included in ntfsprogs and is called ntfsmount

i.e. 

```
sudo apt-get install ntfsprogs
```then run 

```
[ALT][F2] ntfsmount
```Otherwise, see if this line works in /etc/fstab (make sure the mount point exists!)

```
/dev/sbd1 /media/externalHD ntfs-3g defaults,locale=en_US.utf8 0 0
```

---

### Post by CrimsoniteX on 2011-01-04
> **seawolf167 said:**
> Take a look at the link to fstab in my sig

Thank you! I followed the link, used Pysdm, and everything is working as it should :-)

---

