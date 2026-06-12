---
title: "Bad line in fstab"
date: 2011-11-14
forum: General Help
---

### Post by arcelivez on 2011-11-14
Hi,

I'm getting the following error message, while trying to mount folders which have spaces in their name:

arturas@Universe:~$ sudo mount -a
[mntent]: line 24 in /etc/fstab is bad

And the line in /etc/fstab looks like this:

/mnt/Storage_drv/all_files/All\ Files /home/arturas/Downloads/All\ Files xfs rw,bind 0 0

I also tried changing to:
/mnt/Storage_drv/all_files/All\ Files/ /home/arturas/Downloads/All\ Files/ xfs rw,bind 0 0
(added the slashes after the locations) but no difference.

Any ideas? Thanks?

---

### Post by arcelivez on 2011-11-15
Any help would be appreciated... ;)

---

### Post by hansdown on 2011-11-15
Hi, arcelivez.

I wanted, to answer your first post, but am not knowlegable.

I'm only guessing, that the backward slashes, are a hinderance.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by drs305 on 2011-11-15
In fstab spaces are written as \040.

A folder called "My Documents" would be written as **My\040Documents**
So if the mountpoint was on /mnt, it would be written as /mnt/My\040Documents

---

### Post by matt_symes on 2011-11-15
Hi

I'm pretty sure you need the octal code for a space. Try this.

```
/mnt/Storage_drv/all_files/All\040Files /home/arturas/Downloads/All\040Files xfs rw,bind 0 0
```

Kind regards

---

### Post by arcelivez on 2011-11-16
Thanks a lot guys! ;)
The \040 trick worked!

---

