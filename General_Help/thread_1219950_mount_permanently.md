---
title: "mount permanently"
date: 2009-07-22
forum: General Help
---

### Post by zeker446 on 2009-07-22
i there i have a storage with samba pdc ,and in my computer i mount this way the folder

sudo mount -t smbfs //192.168.5.204/y /media/y -o username=root,uid=www-data,gid=www-data,oid=www-data

but i need to mount it permanently, i tried in fstab but it won't mount on boot 



thanks in advance

---

### Post by Cheesemill on 2009-07-22
Post your fstab file so we can see where the mistake is.

---

### Post by nikhilk on 2009-07-22
> **zeker446 said:**
> i there i have a storage with samba pdc ,and in my computer i mount this way the folder

sudo mount -t smbfs //192.168.5.204/y /media/y -o username=root,uid=www-data,gid=www-data,oid=www-data

but i need to mount it permanently, i tried in fstab but it won't mount on boot

Try to workaround it by adding noauto to the options in the corresponding line in fstab. Then add the mount command in "System->Preferences->Statup Applications" to mount it e.g. mount /media/<mount name>. Or you can put the mount command in a script and add that script to "Statup Applications".

---

### Post by zeker446 on 2009-07-22
//192.168.5.204/y    /media/y    smbfs    username=root,password=***,uid=www-data    0    0

---

### Post by prem1er on 2009-07-22
No, post the entire file in the ```
 brackets.  

[CODE]nano /etc/fstab
```

---

### Post by zeker446 on 2009-07-22
proc            /proc           proc    defaults        0       0
UUID=244da247-278d-4983-9b21-0892843c0842 /               ext3    relatime,errors=remount-ro 0       1
UUID=e0a590d1-e34e-4bb6-bdd6-79b94f031a55 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
//192.168.5.204/y    /media/y    smbfs    username=root,password=***,uid=www-data    0    0

---

### Post by KeyserSoze93 on 2009-07-22
Try:

```
//192.168.5.204/y		/media/y	cifs	auto,iocharset=utf8,user=root%***,uid=www-data,gid=www-data	0 0
```

---

### Post by zeker446 on 2009-08-03
thanks solved

---

