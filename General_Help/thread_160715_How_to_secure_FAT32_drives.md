---
title: "How to secure FAT32 drives"
date: 2006-04-15
forum: General Help
---

### Post by wyo on 2006-04-15
I just tried to write into a FAT32 drive (mounted as vfat) but the security doesn't allow it. Fine I started Nautilus as root but again no rights. So how do I change the rights?

O. Wyss

---

### Post by taurus on 2006-04-15
How do you mount that partition?  Do you mount it by hand, from a terminal, or do you have it mount automatically upon boot in /etc/fstab?  If you use /etc/fstab to mount it, look in there and perhaps you need to add this "umask=0000" after the defaults so an entry for your fat32 would look something like
```

/dev/hda2  /backup  vfat  defaults,umask=0000  0  0

```

---

### Post by aysiu on 2006-04-15
taurus is right.

Here are a couple of tutorials that walk you through it step by step:

Abbreviated:
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

More detailed:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by jazzmuzik on 2006-04-15
To be a little more secure you can make the vfat drives writable only to yourself:

```
/dev/hda2  /backup  vfat  uid=0,gid=499,umask=002  0  0
```

Then create a group called 'vfat' (group id 499) and then add yourself to that group.

---

