---
title: "How to change my password for my /home partition?"
date: 2012-05-23
forum: General Help
---

### Post by Welly Wu on 2012-05-23
Hi. I have an ASUS N61JV-X2 notebook PC with 8 GB of dual-channel DDR3 PC-8500 SDRAM and an Intel 2nd Generation MLC NAND FLASH X25-M 160 GB Solid State Drive running Ubuntu 12.04 64 bit Long Term Support GNU/Linux. I used LUKS/LVM with the Serpent cipher in CBC ESSIV SHA-256 mode at 256 bits cipher strength and SHA-512 hash algorithm to encrypt most of my Intel X25-M SSD. When I first booted into Ubuntu a few weeks ago, it asked me to create a password for my /home partition. I want to change the password for my /home partition now to a much stronger password. How do I do this?

I tried ecryptfs-setup-private, but it keeps telling me that my /home partition is mounted. How do I dismount my /home partition safely so that I can change the password using this command?

I tried using Cryptkeeper, but it seems that it wants to create a new encrypted partition which is not something that I am interested in at all.

How do I change the password for my /home partition safely so that I can log in and log out and access it normally?

I have three partitions: 1. 8 GB /swap partition, 2. 52 GB /root partition, 3. 98 GB /home partition. They are in volumegrp-01 with three separate volumes named volume01, volume02, and volume03 which represent the /swap, /root, and /home partitions respectively. It's /dev/volumegrp-01/volume03 which is my /home partition that I want to change my encrypted password.

Please help me if you can. This is very important to me. Thanks.

---

### Post by Welly Wu on 2012-05-23
[http://ubuntuforums.org/archive/index.php/t-1223354.html](http://ubuntuforums.org/archive/index.php/t-1223354.html)

ecryptfs-rewrap-passphrase /home/.ecryptfs/$USER/.ecryptfs/wrapped-passphrase

This is what did it for me. Now, I have to log out and test my changes.

---

### Post by Welly Wu on 2012-05-23
I also learned that typing in passwd wellywu will also change my encrypted /home partition passphrase as well. To use the GUI, click on the About Me icon and authenticate and change your password and your encrypted /home partition passphrase will be updated as well.

---

