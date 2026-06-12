---
title: "Cannot boot after hibernating"
date: 2011-12-20
forum: General Help
---

### Post by arnab321 on 2011-12-20
I tried hibernate for the first time, and after that , on every reboot i get this screen. (attached)

Im using Ubuntu 11.10, and I have a swap partition. I have heard that clearing the swap will delete the hibernate file and may resolve the issue, but I'm not able to boot now.

---

### Post by 2F4U on 2011-12-20
You could boot into a liveCD and use gparted to reformat the swap partition. That should remove anything from the previous hibernate.

---

### Post by matt_symes on 2011-12-20
Hi

You can delete the hibernation image in the swap partition by booting into a LiveCD/USB and formatting your swap partition (assuming you use a partition and not a file), using mkswap on the correct device node.

```
sudo mkswap <device node>
```Check out the switches from the man page to see if any interest you.

You can find the correct device node using

```
sudo blkid
```or

```
sudo fdisk -l
```Kind regards

---

### Post by arnab321 on 2011-12-21
Reformatted swap. It booted. But it seems that hibernate would never work. I clicked on hibernate again. Black screen with a cursor. 
then it said some **ACPI error**. And the PC turned off. I booted again, to find another freezed distorted screen, as in this attachmen.t

The strangest thing is that the blue part of the distorted screen is the wallpaper i have in windows 7. I have a red wallpaper in Ubuntu and it is clearly visible in the bottom right of the screen, with a file thumbnail, also it seems like the its there in the top part of the screen. The text that you see near the bottom is from internet explorer.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=209483&stc=1&d=1324465054[/IMG]

---

### Post by Pilot6 on 2011-12-21
It seems that after a recent update hibernate is broken on some desktop computers. Wait for an update with a fix.

---

