---
title: "Ubuntu going crazy with grub and partitioning"
date: 2009-08-04
forum: General Help
---

### Post by JFlou on 2009-08-04
I recently bought a MSI notebook with Vista Home Premium pre-installed. I wanted to have another OS that was faster and less prone to viruses, so I decided to dual boot Ubuntu 9.04 with Vista. The laptop came out of the box with two partitons of the 320 GB HDD, one that was OS Install of about 44 GB, and Data that was 245 GB. My girlfriend recently made me a live cd of Ubuntu 9.04 that she made custom, so I booted from the live cd and ran GParted to make a 15 GB partition from the 245 GB Data partition. Once the partition was finished, we restarted and installed Ubuntu on the 15 GB partiton and found that grub automatically set up itself after the installation. Everything seemed to work fine except that Ubuntu could not connect to my wireless network (I've posted a thread about this problem elsewhere if you think you can help) and that my speakers were not working except for the subwoofer, which may just need some drivers to work properly (has 4 speakers+1 subwoofer). It seemed like everything was going to work fine until I downloaded and installed updates for Ubuntu. After that, once I restarted my laptop, grub had added an additional boot choice to the menu, as if each update was a different OS. I booted from the most recently updated Ubuntu and Windows Vista just fine, but when I tried to access the others, it tried to load but came up with an error. Not only that, but when I went into GParted to try and remove the partition with Ubuntu to start over, I found that there were at least 2 extra partitions that I didn't recognize. It doesn't seem to hurt the system at all, but it's really perplexing me. Please help if you can.

---

### Post by TeoBigusGeekus on 2009-08-04
The updates installed new kernels for Ubuntu.
Grub keeps older kernels in case something goes wrong with the new ones.
If your system works with the newest one then you don't have a problem.
If it really bothers you watching them in the grub menu, then you could delete the entries
```
gksudo gedit /boot/grub/menu.lst
```

Could the extra partitions be the swap,/home, /var, /bin or something like that?

---

### Post by JFlou on 2009-08-04
Here's what it looks like.

---

### Post by TeoBigusGeekus on 2009-08-04
Here you are

---

### Post by JFlou on 2009-08-04
Oh, okay that makes sense. Thank you! :D

---

