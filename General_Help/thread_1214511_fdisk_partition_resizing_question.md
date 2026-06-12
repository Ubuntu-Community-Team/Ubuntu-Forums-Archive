---
title: "fdisk partition resizing question"
date: 2009-07-16
forum: General Help
---

### Post by zot171 on 2009-07-16
this seems simple and straight forward enough...

if i have 3 (in order) partitions, sda1:ext3, sda2:NTFS, and sda3:swap, and i have cleared all the data from sda2 and wish to expand sda1 (which contains the OS) to encompass the space of sda1 and sda2 with data type ext3, would the data in sda1 be preserved?

in other words...
```
sudo fdisk /dev/sda
d
1
d
2
n
p
1
[default]
[default]
t
1
83
w

```

will my OS on sda1 be preserved? it seems to me that all i would be doing is changing which cylinder on which the partition ends... i just want to make sure before i accidentally wipe valuable information

---

### Post by lindsay7 on 2009-07-16
I would use Gparted to do this. It is much easier to understand and safer as it is graphical.

---

### Post by sdlynx on 2009-07-16
I agree with the above person, and if you do that, yes your data should be fine.  Backup just in case though.

---

### Post by zot171 on 2009-07-16
i dont disagree with the backups, and gparted may be a better choice, but this is a computer that was brought to me by a friend who had trouble with gparted (his experience, not sure why) and im not sure if he kept backups... i just usually use fdisk, im more familiar with it, i use it on my machines, and i simply didnt run into this problem until now...

---

### Post by sdlynx on 2009-07-16
Oh in that case I can't really help, I don't use fdisk for anything except listing partitions

---

### Post by az on 2009-07-16
What you will end up with is a bigger partition, but the filesystem will still be the same size.  You will need to resize the filsystem by hand to take up the rest of the available space.

---

