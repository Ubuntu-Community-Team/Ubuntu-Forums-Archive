---
title: "cd to external drive"
date: 2011-03-28
forum: General Help
---

### Post by Ginger The Cat on 2011-03-28
I have an external drive with lots of photos on. I want to resize them and someone suggested using
```
for f in *.jpg; do convert "$f" -resize 640x480 -strip -quality 86 "$f"; done

```
Then I realised I don't know how to cd to an external drive.

The drive shows up as "Iomega HDD" in Nautilus.

I tried every variation I could think of including creating a mount point on my home partition.

Can anyone help me with the correct syntax

Thanks

Mike

---

### Post by TeoBigusGeekus on 2011-03-28
The mount points of your external hds are located in your /media folder.
Can you post us the output of 
```
ls /media
```
?

---

### Post by Ginger The Cat on 2011-03-28
0852-94EC
DJ_AIO_06_F4500_
Iomega HDD
OS
sda1
sda3

---

### Post by TeoBigusGeekus on 2011-03-28
Excellent!!
Give
```
cd "/media/Iomega HDD"
```
and you're done.
(I've put quotes to the path because of the space in the name of your hd).

---

### Post by Ginger The Cat on 2011-03-28
Excellent.

Thanks a million :)

---

