---
title: "&quot;Read-only file system&quot; and &quot;expunged&quot; folder."
date: 2010-10-14
forum: General Help
---

### Post by Light-kun on 2010-10-14
Hi, guys.
few days ago I mentioned that I can't write to my SD-card because of this error:
"Read-only file system"
tried to remount, but -no way.
```
[drey@local ~]sudo umount -v /sd
/dev/sdc1 umounted
[drey@local ~]sudo mount -v /sd
/dev/sdc1 on /sd type vfat (rw,noexec,nosuid,nodev,noatime,nodiratime,uid=1000,gid=1000,iocharset=utf8)
[drey@local ~]

```
```
$ cat /etc/fstab|grep "/sd"
/dev/sdc1      /sd     vfat    auto,rw,users,noatime,nodiratime,uid=drey,gid=drey,iocharset=utf8 0 0

```

/var/log/messages when i unmounted and plugged off then plugged in again my SD-card:
```
tail -f /var/log/messages
# unmount
# plug off
Oct 14 08:51:04 santas-lil-helper kernel: [48896.640266] usb 5-5: USB disconnect, address 2
# plug in again
Oct 14 08:51:11 santas-lil-helper kernel: [48903.600100] usb 5-5: new high speed USB device using ehci_hcd and address 6
Oct 14 08:51:11 santas-lil-helper kernel: [48903.734778] usb 5-5: configuration #1 chosen from 1 choice
Oct 14 08:51:11 santas-lil-helper kernel: [48903.735488] scsi4 : SCSI emulation for USB Mass Storage devices
# auto mount worked
Oct 14 08:51:16 santas-lil-helper kernel: [48908.733051] scsi 4:0:0:0: Direct-Access     Single   Flash Reader     1.00 PQ: 0 ANSI: 0
Oct 14 08:51:17 santas-lil-helper kernel: [48909.198632] sd 4:0:0:0: [sdc] 32235520 512-byte hardware sectors: (16.5 GB/15.3 GiB)
Oct 14 08:51:17 santas-lil-helper kernel: [48909.199525] sd 4:0:0:0: [sdc] Write Protect is off
Oct 14 08:51:17 santas-lil-helper kernel: [48909.203225] sd 4:0:0:0: [sdc] 32235520 512-byte hardware sectors: (16.5 GB/15.3 GiB)
Oct 14 08:51:17 santas-lil-helper kernel: [48909.203977] sd 4:0:0:0: [sdc] Write Protect is off
Oct 14 08:51:17 santas-lil-helper kernel: [48909.204050]  sdc: sdc1
Oct 14 08:51:17 santas-lil-helper kernel: [48909.207460] sd 4:0:0:0: [sdc] Attached SCSI removable disk
Oct 14 08:51:17 santas-lil-helper kernel: [48909.207606] sd 4:0:0:0: Attached scsi generic sg2 type 0

```

and still can't write.

Mentioned also some strange folders like "expunged":
```
ll /sd
ls: cannot access /sd/expunged: Input/output error
total 68K
drwxr-xr-x 10 drey drey 8.0K 1970-01-01 08:00 ./
drwxr-xr-x 22 root root 4.0K 2010-07-27 16:32 ../
drwxr-xr-x  2 drey drey 8.0K 2009-06-19 12:53 .disk/
drwxr-xr-x  2 drey drey 8.0K 2010-09-29 10:02 downloads/
d?????????  ? ?    ?       ?                ? expunged/
drwxr-xr-x  7 drey drey 8.0K 2010-09-16 05:57 music/
drwxr-xr-x 10 drey drey 8.0K 2010-08-26 19:11 photos/
drwxr-xr-x  2 drey drey 8.0K 2010-09-13 13:47 torrents/
drwxr-xr-x  5 drey drey 8.0K 2010-09-29 10:05 .Trash-1000/
drwxr-xr-x  3 drey drey 8.0K 2010-10-07 09:53 video/

``` 

How I can  mount this disk RW to erase "expunged" (I think it will do the trick)?

---

### Post by SlugSlug on 2010-10-14
what does 

sudo chmod 777 /sd  


do?

can you then sudo rm /sd/expunged/ -Rf  to wipe it off?

---

### Post by Light-kun on 2010-10-14
> **SlugSlug said:**
> what does 
sudo chmod 777 /sd  

Obviously it outputs this:
```
chown: changing ownership of `/sd': Read-only file system
```

btw, sudo fisdk -l |grep -A99 "sdd"
```
Disk /dev/sdd: 16.5 GB, 16504586240 bytes
255 heads, 63 sectors/track, 2006 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d410d40

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        2007    16113664    c  W95 FAT32 (LBA)
```

and mount|grep sdd
```
/dev/sdd1 on /sd type vfat (rw,noexec,nosuid,nodev,noatime,nodiratime,uid=1000,gid=1000,iocharset=utf8)

```

Even windows can't mount this SD-card properly (it doesn't even see it in administration->computer->hard disk drives, when plugged in).

---

### Post by Light-kun on 2010-10-18
Thanks for a good idea - check write-protection lock on sd-card:

After I switched this lock and tried to mount I've immediately got read-only FS (after mount). dismounted, switched lock back and mounted RW finally. After it I had to format this drive to remove "expunged". After formatting I have no problems.:popcorn:

---

