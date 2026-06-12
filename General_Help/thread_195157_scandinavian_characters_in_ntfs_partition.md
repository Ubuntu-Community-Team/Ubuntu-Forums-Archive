---
title: "scandinavian characters in ntfs partition"
date: 2006-06-12
forum: General Help
---

### Post by User-007 on 2006-06-12
Hi all,

Scandinavian characters are seen correctly in linux filesystems (using reiserfs). However, they are not seen OK in NTFS. I think this can be due to mounting NTFS.There is a line according to general guide in my /etc/fstab:

/dev/hda1    /media/win_f ntfs  nls=utf8,umask=0222 0    0 . 

Maybe i have to change "utf-8" to some other charset. What are the other alternatives?

I will appreciate your help.

User JB

---

### Post by t3r0 on 2006-06-12
hi

Most likely your windows partition is iso8859-1...

Here is a line from my fstab, with working charset in a vfat  partition

```

/dev/hdb5 /home/t3r0/data vfat  iocharset=iso8859-1,uid=1000  0 0

```


Hope this helps,

 -Tero

---

### Post by User-007 on 2006-06-13
Hi,

my /etc/fstab looks now like
/dev/hda7       /mnt/win_f      ntfs    nls=iso8859-1,umask=0222 0    0

However, scandinavian characters don't appear correctly after reboot. Any ideas or suggestions?

User JB

---

### Post by User-007 on 2006-06-13
Any suggestions?

---

### Post by t3r0 on 2006-06-15
[QUOTE=User-007]Any suggestions?[/QUOTE]


Hi

did you try with the "iocharset" option ?

In your case:

```

/dev/hda1 /media/win_f ntfs iocharset=iso8859-1,umask=0222 0 0

```



 -Tero

---

### Post by User-007 on 2006-06-15
Hi,

I have not tried it yet. I have thought that "iocharset" option is only for fat filesystems. Please inform me if this is not true.

However, I will give a try for this suggestion later.

User JB

---

### Post by User-007 on 2006-06-16
I have now tried your suggestion, t3r0. It didn't solve the problem. Maybe this is not an issue related to mounting?

User JB

---

