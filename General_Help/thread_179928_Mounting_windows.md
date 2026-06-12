---
title: "Mounting windows"
date: 2006-05-21
forum: General Help
---

### Post by YumZ on 2006-05-21
I did
```
sudo mkdir /media/windows
```
then
```
sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000
```
but I got this:
```
mount: wrong fs type, bad option, bad superblock on /dev/hda1, missing codepage or other error
In some cases useful info is found in syslog - try dmesg | tail  or so
```

I have also tried
```
sudo gedit /etc/fstab
```
then
```
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0
```
That didn't work either.....

---

### Post by Kethinov on 2006-05-21
You sure it's a vfat volume?

Place this line in your **/etc/fstab** (ensure no other lines for /dev/hda1 exist), save it, then **cd /media** and **sudo mount windows**

```
/dev/hda1       /media/windows   ntfs    user,ro,umask=000       0       0
```

---

### Post by Ramses de Norre on 2006-05-21
```
sudo fdisk -l
``` will show you which filesystem you've got on the drive.

---

### Post by YumZ on 2006-05-21
Problem solved.....It showed up when I rebooted.

---

