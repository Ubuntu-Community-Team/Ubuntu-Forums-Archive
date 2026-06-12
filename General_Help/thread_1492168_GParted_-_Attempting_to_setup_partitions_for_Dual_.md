---
title: "GParted - Attempting to setup partitions for Dual Boot"
date: 2010-05-24
forum: General Help
---

### Post by FinalShot on 2010-05-24
I want to dual boot Windows XP, but I can't resize my ext4 partition, is there a way to resize it?

[img]http://img541.imageshack.us/img541/2312/screenshotdevsdagparted.png[/img]

---

### Post by SlidingHorn on 2010-05-24
How are you attempting to resize your partition?  This can usually be done using the liveCD without issue

---

### Post by FinalShot on 2010-05-24
Ah never mind about the resizing, but is this the correct way to dual boot xp after 9.10 is installed?

Install XP on a partition, then boot xp not ubuntu.
Then reinstall Grub from the live cd: [correct?](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

And that's it?

---

### Post by oldfred on 2010-05-24
Just make sure you create a primary partition for windows and it has to have the boot flag. Linux does not use the boot flag, but some BIOS require a boot flag on a primary partition.

If you have a new install your instructions are correct for reinstalling grub2 after a windows install. If you have an upgrade with grub legacy then you need the instructions for grub legacy.

---

### Post by FinalShot on 2010-05-24
Done all that, but when I try to update I get this error:
```
ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.

```

And I mounted my partition with grub on it again ( sda1 ).

---

### Post by oldfred on 2010-05-24
You run the sudo update-grub after you have installed grub2 and rebooted to find the other systems. If you have to run it from a liveCD then you have to chroot into your system. You should be just able to reinstall grub & boot. Then run the update to find the windows install.

---

### Post by FinalShot on 2010-05-25
I didn't realized I had to boot into Ubuntu ( not live cd ).

---

