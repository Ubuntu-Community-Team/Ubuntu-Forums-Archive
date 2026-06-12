---
title: "Labels in Nautilus/Computer do not work"
date: 2006-05-06
forum: General Help
---

### Post by foxy123 on 2006-05-06
I have a strange problem. If I insert a CD into my CD-ROM or CD/DVD-ROM, go to Places/Computer and click on 'CD-ROM Drive' or 'CD-RW/DVD±R Drive' label there, I;ve got the following error:
```
Unable to mount the selected volume.
mount: block device /dev/hdd is write-protected, mounting read-only
mount: /dev/hdd already mounted or /media/cdrom1 busy
mount: according to mtab, /dev/hdd is already mounted on /media/cdrom1
Error: could not execute pmount

```

I can access the CD through /media/cdrom1, but it is slightly annoying not to be able to access it through the labels.

my fstab section looks like that:
```
/dev/hdc        /media/cdrom0   udf,iso9660 users,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 users,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,users,noauto  0       0

```

BTW, floppy label works fine.

Any help please?

---

