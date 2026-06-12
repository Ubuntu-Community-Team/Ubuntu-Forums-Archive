---
title: "FML... Three strikes with LVM/EXT4 :("
date: 2010-08-24
forum: General Help
---

### Post by modmadmike on 2010-08-24
I have a Logical Volume named "Bulk_Store" which spanned 3 drives (1 SATA 250GB, 1 SATA 500GB, and one IDE 250GB), when a broken usb device shorted the system, the power supply instantly cut power. After unplugging the device I thought everything was okay until I tried downloading a file... Checked my Downloads symlink and found that it still pointed to /Bulk_Store/Downloads, but the folder was empty and read only... The IDE drive that was part of the LVM array was completely fried and undetected by both the bios and the kernel!!!!  :( And that was not the end because I redid the LVM array and within 24 hours the 250GB SATA had bad sectors!!! SO I DID IT AGAIN!!!! This time the 500GB drive got bad sectors after downloading the same file (android-sdk-linux)!!!! MY LOVE FOR LVM HAS FAILED ME :(!! This time I am doing a zero fill first!!!

---

