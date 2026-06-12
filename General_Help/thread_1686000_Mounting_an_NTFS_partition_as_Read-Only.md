---
title: "Mounting an NTFS partition as Read-Only"
date: 2011-02-11
forum: General Help
---

### Post by rick astley on 2011-02-11
Hi all,

I have successfully mounted the NTFS partition containing win7 via Ubuntu. I followed these 3 steps:

[FONT="Fixedsys"]```
# sudo mkdir -p /media/win
# sudo fdisk -l
# sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/sda2 /media/win
```[/FONT]

Now I have unmounted the partition and want to remount it again except this time so that it is mounted as Read-Only.
How can I achieve this?
Thanks.

---

### Post by rick astley on 2011-02-11
I figured out a solution..

```
# sudo mount /media/win -o remount,ro,noatime
```

it's important that there are no spaces between the remount,ro,noatime options. The noatime option means no access times are permitted to change.

rick.

---

