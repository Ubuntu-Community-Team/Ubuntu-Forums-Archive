---
title: "Wrong permissions for drive acess"
date: 2006-01-26
forum: General Help
---

### Post by AvvY on 2006-01-26
I have two SATA drives which I use for data. Each of these are auto mounted on boot, but when in Ubuntu I cannot view their contents because I do not have permissions (acording to an error message).

I went into fstab and had a look. Both drives were set to "default" so I threw in some other options "ro,auto,user" but this didn't work either. Both drives are NTFS. I know I can only have readonly access, but I need it.

Thanx

---

### Post by niccolo.canestrari on 2006-01-26
I use this line in the fstab: 

/dev/hdb1       /media/windows  ntfs    **nls=utf8,umask=0222** 0       0

---

### Post by AvvY on 2006-01-26
Thanx mate, it worked perfectly! I use to know how to do this stuff, but havn't used Ubuntu in a few months and I forgot the options, cheers anyhow!

---

