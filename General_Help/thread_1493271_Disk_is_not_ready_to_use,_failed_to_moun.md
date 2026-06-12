---
title: "Disk is not ready to use, failed to moun"
date: 2010-05-25
forum: General Help
---

### Post by ciaastek on 2010-05-25
Hi. I get this error on plymouth:

> The disk drive for /media/Windows7 is not ready yet or not present.
Continue to wait; or Press S to skip mount or M for manual recover

To be honest I don't really know what caused that issue because I just saw it the day after and I thought that it happened itself so it'll be gone by itself. Sadly - it didn't. Anyway there's one easy way to get rid of this problem - disable auto-mount this disk (checked when I installed Ubuntu) but don't really know how ^^'

---

### Post by ciaastek on 2010-05-25
bump ^^'

---

### Post by ciaastek on 2010-05-25
Okay, I just ask you people one thing, which I think is simple to most users. How I can disable auto mount of one of windows' partition?

---

### Post by ciaastek on 2010-05-26
bump 

please!

---

### Post by WorMzy on 2010-05-26
Please don't bump a topic until 24 hours has passed, by bumping you may well have robbed yourself of help as there's a team on these forums which actively seeks out topics which have no replies to provide assistance, by bumping, you've stopped your topic showing up in their searches.

The best way to stop a partition from automounting is to comment out the line that makes it get mounted from /etc/fstab.

For example, my ntfs storage partition is mounted with the following line:
```
UUID=7A5C94995C94522D /media/Terastore ntfs user,uid=1000,gid=1000,umask=007,dmask=007,fmask=007,exec,rw 0 0
```

To stop it automounting, all I would need to do is add a "#" at the start of the line, to make it into a comment:
```
#UUID=7A5C94995C94522D /media/Terastore ntfs user,uid=1000,gid=1000,umask=007,dmask=007,fmask=007,exec,rw 0 0
```

---

### Post by ciaastek on 2010-05-26
> Please don't bump a topic until 24 hours has passed, by bumping you may well have robbed yourself of help as there's a team on these forums which actively seeks out topics which have no replies to provide assistance, by bumping, you've stopped your topic showing up in their searches.
Okay, I'll remember that, sorry.

Anyway thanks for reply. And ofcourse that solved my problem. There was two lines for mounting this partition. I deleted one of them and now it works great :D so today I learned two things, thanks :)

---

