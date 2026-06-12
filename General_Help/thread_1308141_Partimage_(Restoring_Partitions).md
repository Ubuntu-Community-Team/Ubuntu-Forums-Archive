---
title: "Partimage (Restoring Partitions)"
date: 2009-10-31
forum: General Help
---

### Post by Feelin_froggy8877 on 2009-10-31
I decided to do some repartitioning To my Desktop Comp due to not enough free space in /root dir. I used Partimage to backup/restore. The total space used for /root was 1.92G (used blocks copied) and /Home was 2.68G.(used blocks copied) I repartitioned a larger hdd for /root, /home and swap. Its a 120g hdd. Gave /root 20G, /home 92.89G. For some reason partition editor is reporting 18.76G used on /root and 79.25G used on home.  In theory there should only be 1.92 used on root and 2.68 used in home.  Any ideas what the deal is here?

---

### Post by Feelin_froggy8877 on 2009-10-31
I started to redo the process of restoring to see if I could have missed something, I noticed an option for "erase free blocks w/ zero values" Could this be the option I need to check for restoring to a larger partition?

---

### Post by Feelin_froggy8877 on 2009-10-31
o.k seems you cannot use a larger partition for restore. Did a lil digging and found "sudo ddrescue -v /dev/sdb /dev/sda" Worked very well. After the copying was complete just did a resize/move on the new partitions and everything is great. Successfully  copied my /root and /home partitions to a completely different hdd. Partimage is great as well, so long as your only doing a restore to same size partitions. I also had to do a grub restore witch was not a problem at all.

From a term...

sudo grub

<grub find /boot/grub/stage1
"(hd0,0)"

<grub root (hd1,0)

<grub setup (hd0)

---

