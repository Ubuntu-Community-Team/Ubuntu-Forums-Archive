---
title: "Ubuntu claims CDROM not mounted when looking for files for installation ..."
date: 2010-07-06
forum: General Help
---

### Post by lhcpr on 2010-07-06
Hi all,

When I am 'apt' command to get/install programs, when it queries files from CDROM as a repository, I get the message:

```
Put CDROM labeled [Ubuntu_10.04_LTS__Lucid_Lynx__-_Release_i386_(20100429)] in the cdrom device
read: 1: arg count
mount: can't find /cdrom in /etc/fstab or /etc/mtab
cp: cannot stat `/cdrom/dists/lucid/Contents-i386.gz': No such file or directory
umount: /cdrom: not mounted

```

The disk is mounted on device /dev/sr0 at /media/cdrom and a desktop icon is present. FSTAB reads:
```
/dev/sr0 /media/cdrom	udf,iso9660	rw,user,nosuid,nodev	0 0
```

Also, when I go to 'Add CD-ROM' in the "Other Software" tab of software sources, I am prompted to insert a disk. Clicking ok with disk in --> ```

E:Failed to mount the cdrom
```

Any ideas about this issue??? I'm beat

Cheers - Graham

---

