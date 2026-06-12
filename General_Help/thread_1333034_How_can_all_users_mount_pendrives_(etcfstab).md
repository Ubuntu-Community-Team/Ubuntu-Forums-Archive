---
title: "How can all users mount pendrives (/etc/fstab)"
date: 2009-11-21
forum: General Help
---

### Post by frenchn00b on 2009-11-21
How can all users mount pendrives (/etc/fstab)

---

### Post by frenchn00b on 2009-11-21
this shall be added for /etc/fstab
fdisk -l /dmesg gives the listing of disks 

works for all vfat

```
 /dev/sda1       /mnt/sda1       vfat    user,rw,auto,umask=0000,uid=1000,gid=1000  0    2 
```

---

### Post by jocko on 2009-11-21
You don't mount a pendrive through fstab.
Just make your users member of the plugdev group:
```
sudo adduser [COLOR=Blue]username[/COLOR] plugdev
```

---

