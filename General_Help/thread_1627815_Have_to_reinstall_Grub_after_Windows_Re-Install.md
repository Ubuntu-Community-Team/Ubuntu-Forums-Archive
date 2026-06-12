---
title: "Have to reinstall Grub after Windows Re-Install"
date: 2010-11-21
forum: General Help
---

### Post by The Thunder Chimp on 2010-11-21
I re-installed Windows over an old Windows partition. The hard-drive used to have Windows and Ubuntu on it. I am now in usb live ubuntu because grub doesn't appear anymore when I boot the computer (it boots in the new windows automatically). The ubuntu partition is still there, as I can access my files from this live usb. I'd just like to know how to re-install grub. Thanks!

---

### Post by drs305 on 2010-11-21
If you are using Grub2 (there would be a grub.cfg file in /boot/grub):

From the LiveCD, mount your Ubuntu partition. Often on a dual install it is located on sda5. I'll use that in the example but *you must change it to match your actual Ubuntu partition.* If you aren't sure which one it is, run "sudo fdisk -l" (lowercase L) and look for the 'Linux' partition.

Mount your Ubuntu partition, then install Grub2. Note the first command uses the partition designation, but the second uses *only* the drive. If the Ubuntu partition is not sda5, change it:
```

sudo mount /dev/sd**a5** /mnt
sudo grub-install --root-directory=/mnt /dev/sd**a**
```

G2 should find your Windows OS and automatically put it in the menu. Reboot and if it is not found, when you are running Ubuntu from a normal boot (i.e. not the LiveCD), run "sudo update-grub".

---

