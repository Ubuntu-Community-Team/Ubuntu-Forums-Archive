---
title: "Bootloader Problems After Removing a Partition"
date: 2011-12-24
forum: General Help
---

### Post by Infamous Blob on 2011-12-24
Hey folks,
I've kinda broken my GRUB bootloader thingee.
I installed Kubuntu alongside Ubuntu, just to sorta evaluate it for a bit. Anyways, decided in the end to stick with Ubuntu so I tried to uninstall Kubuntu... stupidly I downloaded gparted and basically zapped it's partition while inside my Ubuntu installation.
Now when I start the machine, I get just get "the partition does not exist" and then below it "grub rescue>".
I used boot repair from inside a live CD, but it didn't change anything unfortunately. It gave me this output:
[http://paste.ubuntu.com/780872/](http://paste.ubuntu.com/780872/)

Erm... yeah don't know what to do, so all help appreciated :)

---

### Post by coffeecat on 2011-12-24
Your Ubuntu root partition is on sda7, so you need to re-install grub to the mbr of sda so that it looks to sda7. Boot up with a 11.10 Ubuntu live CD and choose "try Ubuntu" to get to the live desktop. Open a terminal, and:

```
sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Reboot and you should be fine.

---

