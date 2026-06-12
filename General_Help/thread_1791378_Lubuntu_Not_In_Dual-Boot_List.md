---
title: "Lubuntu Not In Dual-Boot List"
date: 2011-06-26
forum: General Help
---

### Post by cg2916 on 2011-06-26
I installed Lubuntu, and when I boot up, Lubuntu isn't in my dual-boot options. It may have to do with the fact that I had to manually mess with the partitions in the installer.

I am using XP.

Thanks in advance.

---

### Post by wolfen69 on 2011-06-26
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) go to the section on reinstalling grub.

---

### Post by nzjethro on 2011-06-26
Hi CG, what you should do, is boot from your Ubuntu Live CD, and run update-grub. To do this, boot to your Live CD (by selecting Try Ubuntu from the first screen). Run GParted by typing

```
sudo gparted
```

into a terminal, and identify your Lubuntu partition (it will be of the form sdXX e.g. sda1).

Then, run the following commands in a terminal, substituting your Lubuntu drive for sdY, and your Ubuntu partition for sdXX (e.g. if your Lubuntu partition is sda1, sdXX = sda1, sdY = sda):

```
sudo mount /dev/sdXX /mnt
sudo chroot /mnt
update-grub
grub-install /dev/sdY 
```
NOTE: After executing update-grub, watch the terminal - it will run through your installed kernels, and generate your grub.cfg file. Look for Lubuntu - if it comes up, we're on the right track; if not, we may have some major troubleshooting to do.

Then exit chroot, be hitting ctrl + D. Then type
```
sudo umount /mnt
```

After running these commands, reboot, and hopefully you'll have Lubuntu on you Grub!

---

### Post by cg2916 on 2011-06-26
> **wolfen69 said:**
> [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) go to the section on reinstalling grub.

It worked.

---

