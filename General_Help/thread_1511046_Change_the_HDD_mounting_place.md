---
title: "Change the HDD mounting place"
date: 2010-06-16
forum: General Help
---

### Post by nemiux on 2010-06-16
Hey everyone,
I recently had some problems with mounting one of my HDD partitions made by Windows XP (I have Ubuntu 9.04 installed into my Windows). I got a wonderful solution, by this command I got:

```
sudo mount -t ntfs /dev/disk/by-label/Much /home/nemiux/Desktop/Much
```
This adds all of my partitions files into a directory on the desktop. But I was wondering, is there any way, that I could change the place from my desktop to ```
.../media/Much
``` So that way I could open my HDD normally by clicking Places --> Much

Thanks a lot :)

P.S. Much is my partitions name and nemiux is my user name on ubuntu.

---

