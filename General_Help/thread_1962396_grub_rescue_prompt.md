---
title: "grub rescue prompt"
date: 2012-04-21
forum: General Help
---

### Post by Metul Burr on 2012-04-21
I have a grub rescue prompt. How can i reinstall grub via a usb live?

---

### Post by robgraves on 2012-04-21
if you have a live cd/usb, you can boot into that chroot into the installed partition and reinstall grub
from terminal in live cd enter these commands:
```

sudo mount /dev/sda# /mnt
sudo mount -t proc none /mnt/proc
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /sys /mnt/sys
sudo chroot /mnt
sudo grub-install /dev/sda
sudo update-grub
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
sudo reboot

```
whereas sda# on first command, replace # with actual number of partition

---

### Post by Metul Burr on 2012-04-21
ok now i went to go into the live USB and i got a bt login: prompt. Can't figure out how to get to the live USB now?

---

### Post by robgraves on 2012-04-21
appended above

---

### Post by robgraves on 2012-04-21
> **Metul Burr said:**
> ok now i went to go into the live USB and i got a bt login: prompt. Can't figure out how to get to the live USB now?

I'd imagine you'd have to use the username and password that you created on install...

---

### Post by Metul Burr on 2012-04-21
i didn't have the option to put in user name or password on install. It completed the install and said to take out USB and reboot. I rebooted and got an error with grub rescue and put the live in and got the bt login prompt. It's back track 5.

---

### Post by robgraves on 2012-04-21
found answer here:
[http://www.backtrack-linux.org/forums/showthread.php?t=40293](http://www.backtrack-linux.org/forums/showthread.php?t=40293)

try login: root
password: toor

---

### Post by Metul Burr on 2012-04-21
YES. Thanks that works.

---

