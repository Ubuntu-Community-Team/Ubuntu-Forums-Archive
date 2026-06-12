---
title: "automount NTFS in Lucid - short way?"
date: 2010-05-16
forum: General Help
---

### Post by molar on 2010-05-16
I see a lot of threads on auto mount NTFS in other versions, is it still that cumbersome in Lucid? thx.

---

### Post by Ozymandias_117 on 2010-05-16
Are you talking about automatically mounting an internal HDD/Partition on boot? Or automatically mounting an external hard drive? An external hard drive should already auto mount. If you want an internal auto mounted post back with the results of:

```
sudo fdisk -l
```

---

### Post by dino99 on 2010-05-16
install mountmanager and set your prefs

---

### Post by karthick87 on 2010-11-07
Install ntfs-config it will help you to automount your NTFS partitions

```
sudo apt-get install ntfs-config
```

---

### Post by Morbius1 on 2010-11-07
If your partition is for example a Windows system partition at /dev/sda1:

Make a home for the partition to live in:
```
sudo mkdir /media/WinC
```Add a line to /etc/fstab:
```
/dev/sda1 /media/WinC ntfs defaults 0 0
```Save the fstab file. Then test for errors and mount the new partition by running:
```
sudo mount -a
```3 steps. Is this really that hard? For some apparently it's second only to passing a combinatorics final exam. :wink:

---

### Post by karthick87 on 2010-11-07
See the post below

[http://ubuntuforums.org/showthread.php?t=802699](http://ubuntuforums.org/showthread.php?t=802699)

---

