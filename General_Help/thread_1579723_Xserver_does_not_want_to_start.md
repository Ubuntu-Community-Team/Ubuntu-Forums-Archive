---
title: "Xserver does not want to start"
date: 2010-09-22
forum: General Help
---

### Post by m4tic on 2010-09-22
Upon bootinh ubuntu the display refuses to start, i archived the log files but i don't know how to post them here, im on a windows dual boot

---

### Post by linux-hack on 2010-09-22
Did you try ```
dpkg-reconfigue xserver-xorg 
```

---

### Post by linux-hack on 2010-09-22
whell you copy the log file in the windows partition like this :

first get the partition name lets say (/dev/sda1)

to find out the partiton name you do a :
```
sudo fdisk -l
```

you mount 'it with : 
```
sudo mount /dev/sda1 /mnt
```
then you copy your file with : 
```
cp path_to_file/file /mnt/WHERE_YOU_WANT_TO_COPYit
```

---

