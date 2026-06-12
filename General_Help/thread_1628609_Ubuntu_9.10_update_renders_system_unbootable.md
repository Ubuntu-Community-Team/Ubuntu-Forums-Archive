---
title: "Ubuntu 9.10 update renders system unbootable"
date: 2010-11-22
forum: General Help
---

### Post by s3a on 2010-11-22
My mom's computer is no longer bootable. I was thinking of attempting to fix it later on this week and am thinking of doing a chroot and updating via a live CD hoping that an even newer update solves the problem but I have some doubts of success. Does anyone have any information about this issue so that I can be better prepared to fix it? Also, I thought I should mention that I tried the second newest kernel to see if that would make it work. It didn't. The error is something along the lines of having the /dev/diskuuid change. If I'm correct, Ubuntu changed the disk's name and is trying to boot the old name. It's dropping to an initramfs shell (not the regular terminal where you can work miracles :( ).

Any help would be greatly appreciated!
Thanks in advance!

P.S. Actually it might not be an update that ruined things but then I'm really not sure what it would be.

---

### Post by s3a on 2010-11-24
Nobody else got this problem?

---

### Post by Quackers on 2010-11-24
If it's a UUID problem and you chroot into the system via live cd wouldn't sudo update-grub do some good?
If it's a package problem you could run ```
sudo dpkg --configure -a
sudo apt-get install -f
``` and see what turns up.

---

### Post by s3a on 2010-11-26
I did *sudo update-grub && sudo apt-get update && sudo apt-get dist-upgrade -V && sudo update-grub* and now it works!

---

