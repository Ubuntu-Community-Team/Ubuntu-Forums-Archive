---
title: "Mount, fstab and mysql"
date: 2006-06-28
forum: General Help
---

### Post by bohboh on 2006-06-28
I have mysql installed ok. I have managed to point the data directory (directory with all databases) to my fat32 share so i can share it with xp. I have created a symbolic link from

/etc/lib/mysql to /windows/mysql/Program Files/wamp/mysql/data

In phpmyadmin it can see the database BUT it can't see any tables.

Reason is that the share is not owned by mysql but by me.

In fstab i have set the uid and gid to mysql but it still keeps mounting as me:

```

/dev/sda5	/windows/share	vfat	auto,user,rw,uid=1000,gid=100,umask=0000,codepage=850	0	0
/dev/sda5	/windows/mysql	vfat	auto,user,rw,uid=mysql,gid=mysql,umask=0000,codepage=850	0	0

```

The first line is the normal mount with me as owner, the second is the one for mysql. I have also tried replacing the uid and gid with the number values.

Basically, how do i mount a drive with the owner/user set to mysql so the mysql server can see all databases?

Thanks

---

### Post by bohboh on 2006-06-28
Fixed.

Needed a reboot. ;)

---

