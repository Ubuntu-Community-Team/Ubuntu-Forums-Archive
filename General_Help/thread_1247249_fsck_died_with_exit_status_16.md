---
title: "fsck died with exit status 16"
date: 2009-08-22
forum: General Help
---

### Post by Ahrim on 2009-08-22
I tried to install grub2 over grub 1, ended up restarting to Error 15.

After a few attempts to fix this I decided to try and reinstall grub all together.

From a 9.04 live cd (Karmic is on my main partition)

sudo mkdir /media/sda1
sudo mount -t ext3 /dev/sda1 /media/sda1
sudo mount --bind /dev /media/sda1/dev
sudo chroot /media/sda1
sudo grub-install /dev/sda
sudo update-grub

exit

Restart and the error 15 is no longer there and it tries to boot ubuntu.

Then it fails half way through boot:

fsck died with exit status 16

:confused:

Help would be really appreciated!

---

### Post by Ahrim on 2009-08-22
Fixed it myself.

UUID's were screwed up in fstab.

---

