---
title: "FreeBSD install mangled the boot process"
date: 2010-05-29
forum: General Help
---

### Post by josephrockz4 on 2010-05-29
Hello everyone. I have a problem.
Earlier today, I tried to install FreeBSD. If anyone here has done this, I think I went wrong at the part where it asked if I wanted to edit the Master Boot Record. In any case, now when I turn the computer on, it boots into FreeBSD instead of into GRUB. Now I have no access to Ubuntu or Windows, and I have no internet on FreeBSD. How can I fix the MBR so that it boots into GRUB instead of FreeBSD? I want my Ubuntu back...

For the record, I searched vigorously on the forums and on Google for a solution. I also asked a couple FreeBSD support locations, and they... Didn't help much. I figured this was at least mildly Ubuntu related.

---

### Post by lmarmisa on 2010-05-29
Start your system with an Ubuntu Live CD, open a terminal and type these commands (change /dev/sda1 with the partition where is the root Linux partition if neccesary):

> 
sudo bash
mount /dev/sda1 /mnt
mount --bind /dev /mnt/dev
mount --bind /proc /mnt/proc
chroot /mnt
grub-install /dev/sda
Shutdown the system and reboot without the Live CD.

---

### Post by josephrockz4 on 2010-05-29
> **lmarmisa said:**
> Start your system with an Ubuntu Live CD, open a terminal and type these commands (change /dev/sda1 with the partition where is the root Linux partition if neccesary):

Shutdown the system and reboot without the Live CD.

Thank you so much! It worked perfectly.

---

