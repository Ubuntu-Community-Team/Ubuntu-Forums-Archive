---
title: "change mountpoint of external hd"
date: 2011-02-26
forum: General Help
---

### Post by explodedk on 2011-02-26
hey all.. this might be a noobish question...

i have an external harddisk on my ubuntu minimal installation. it is atm mounted to /media/priv/

i want it to be mounted, or in other way shown in /glftpd/site/archive

---

### Post by Anton K on 2011-02-26
I'm not sure how to change default mount point of the device, but in kind of fast and easy solution you can use symbolic link:
```
ln -s /media/priv /your/archive/point
```
Is it suitable for your tasks?

---

### Post by Hakunka-Matata on 2011-02-26
look at your /etc/fstab file

---

### Post by Hakunka-Matata on 2011-02-26
[http://ubuntuforums.org/showthread.php?t=724227]("http://ubuntuforums.org/showthread.php?t=724227")

talks about your situation

---

### Post by seawolf167 on 2011-02-26
If there isn't an entry in /etc/fstab for that device (i.e. mounting upon boot), then you can simply unmount it

```
sudo umount /media/priv/
```and remount it in the correct location

```

sudo mkdir /glftpd/site/archive
sudo mount /dev/sdXY /glftpd/site/archive
```where sdXY is the drive you want to mount

i.e. from

```
sudo fdisk -l
```If you click the link fstab in my sig it walks you through editing your /etc/fstab file to automatically mount a drive

---

