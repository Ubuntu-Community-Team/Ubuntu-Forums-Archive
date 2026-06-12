---
title: "Splitting partition"
date: 2011-09-19
forum: General Help
---

### Post by Linux_junkie on 2011-09-19
Hi, Just want to know if I can split the main partition so that I can put my home on a separate partition.

---

### Post by gandaran on 2011-09-19
boot the live cd or live usb drive and use gparted to shrink the partition then create another ext4 partition from the unused space
also from the live cd you have to fix the home partition mount point in /etc/fstab or ubuntu wont boot.

---

### Post by seawolf167 on 2011-09-19
Take a look at the [documentation ]("https://help.ubuntu.com/community/Partitioning/Home/Moving")for home to move your /home folder to its own partition.

---

