---
title: "Grub Error 22"
date: 2009-12-07
forum: General Help
---

### Post by apesa on 2009-12-07
Hello,
I am getting the above error in Grub during boot. It will stop and hang there. I searched this site and found a fix "Recover Grub 2 via LiveCD". However I am using the RAID1 mirror via 2x500 Gb HDD's. This is config'd in the BIOS and was handled properly during install and has run well. I have the following configuration. 9.10 64bit, 2 partition drive (/ and /home) using Ext4 filesystem.

The output of fdisk -l shows 2 drives /dev/sda and /dev/sdb while the output of dmraid -r shows

ubuntu@ubuntu:~$ sudo dmraid -r
/dev/sdb: pdc, "pdc_hdbgeifbd", mirror, ok, 976562432 sectors, data@ 0
/dev/sda: pdc, "pdc_hdbgeifbd", mirror, ok, 976562432 sectors, data@ 0

My question is how do I mount the RAID in order to try to get Grub back up and running?

---

