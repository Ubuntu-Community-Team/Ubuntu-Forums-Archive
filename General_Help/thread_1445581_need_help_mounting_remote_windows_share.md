---
title: "need help mounting remote windows share"
date: 2010-04-02
forum: General Help
---

### Post by Mia_tech on 2010-04-02
I'm trying to add an entry to my fstab file to mount a remote windows share... this is what I added

```
//192.168.10.1/netshare	/media/share	cifs	credentials=/root/.credentials,iocharset=utf8,file_mode=0777,dir_mode=0777	0	0
```

```
sudo mount -a
mount: wrong fs type, bad option, bad superblock on //172.16.10.101/share,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by Mia_tech on 2010-04-03
```
sudo apt-get install smbfs
```

---

### Post by zero-g on 2013-03-13
Thanks! Had the same problem

---

