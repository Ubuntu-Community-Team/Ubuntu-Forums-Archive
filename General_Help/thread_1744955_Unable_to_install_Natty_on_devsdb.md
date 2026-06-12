---
title: "Unable to install Natty on dev/sdb*"
date: 2011-04-30
forum: General Help
---

### Post by urosg3 on 2011-04-30
Hi to all
I was unable to install Natty on my slave disk, dev/sdb*. Only  option in installer are dev/sda*.
On the other hand, Gparted recognize all my Hard disks, sda/sdb whatever, and live disk is capable to mount them all.

Any solution for me, please?

Tnx

---

### Post by urosg3 on 2011-05-01
No solution? Strange... Anyway, I think its a bug.

---

### Post by urosg3 on 2011-05-01
Is there any way to install on dev/sdb* please. Run out of ideas

---

### Post by PaulW2U on 2011-05-01
I'm not sure why you're having problems unless a bug has been introduced in the final build. I've installed both Ubuntu and Kubuntu onto my second hard drive many times.

Just make sure you select the "Manual" option and when presented with a list of partitions scroll down so that your sdb partitions are visible. Select where you want your root, home or swap partitions to be and away you go. Obviously check very carefully that you don't select any partitions on your first hard drive and wipe out whatever you have there.

Good luck.

---

### Post by urosg3 on 2011-05-01
[QUOTE=PaulW2U;10753041
Just make sure you select the "Manual" option and when presented with a list of partitions scroll down so that your sdb partitions are visible. Select where you want your root, home or swap partitions to be and away you go. Obviously check very carefully that you don't select any partitions on your first hard drive and wipe out whatever you have there.

Good luck.[/QUOTE]

No way my friend. I`m using Ubuntu since 6.06 and installing many times. There is no way to make sdb visible in install manager. No way, manually, whatever, i do my best, but there is no option at all. My first HDD aka Master is ATA, second aka Slave is Sata. Maybe this is issue?

---

### Post by urosg3 on 2011-05-09
still no solution?

---

### Post by Jouke74 on 2011-05-09
There is a small bug in the installer which will install the MBR Grub program to /dev/sda/. Therefore if you installed on /dev/sdb/ and subsequently remove the USb stick / disk that you installed with, 11.04 won't boot. The trick is to cancel the Grub installation and then supply the new location /dev/sdb to the grub installer.

---

### Post by MichaelSM on 2011-08-16
I had a similar issue, and your explanation resolved it.
Thank you Jouke74.
Mike.

---

