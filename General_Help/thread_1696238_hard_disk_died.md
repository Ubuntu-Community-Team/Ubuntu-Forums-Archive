---
title: "hard disk died?"
date: 2011-02-27
forum: General Help
---

### Post by sumadartson on 2011-02-27
Hi All,


My system decided to crash on me, hard. It was humming along happily for about 2 months and now doesn't boot.

If I boot from hard-disk, I get grub. Launching the first kernel choice hangs. I thought maybe the install was corrupt, so I booted from usb install disk. The usb hdd didn't boot; something about an error trying to access /dev/sda . Unplugging the internal disk and plugging in the usb install disk does result in the system booting. Plugging in the internal disk in a running system usb-booted system does not result in the system detecting the disk. 


- How do I know if the disk is physically broken? This seems unlikely since it does manage to launch grub consistently. Or is this still possible?
- How can I try to mount whatever is left? The usb install disk doesn't even list the /dev/sd* .
- Any pointers on how to reformat the drive if it's not being mounted?

---

### Post by sumadartson on 2011-02-27
HOorah, fixed it. Created another rescue disk with gparted on it. This could see the disk, allowing me to do a filesystem check. After this, no problem.

Slightly disappointed in the fact that my ubuntu usb install disk wouldn't boot with a defective hard-drive. I'm confused.

---

