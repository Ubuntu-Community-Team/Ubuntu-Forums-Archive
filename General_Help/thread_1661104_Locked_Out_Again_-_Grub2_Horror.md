---
title: "Locked Out Again - Grub2 Horror"
date: 2011-01-06
forum: General Help
---

### Post by Quarkrad on 2011-01-06
Back to Grub2 horrors again I'm afriad. Have dual boot winxp and Ubuntu - had to reinstall winxp and so have no grub/ubuntu as MBR rewritten by winxp.  Booting to liveCD this is what my machine looks like:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4462    35840983+  83  Linux
/dev/sda2   *        4463        7169    21743977+   7  HPFS/NTFS
/dev/sda3            7170        7296     1020127+  82  Linux swap / Solaris

Following ubuntu documentation ([https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)) this is what as happened:

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

The documentation does not help re this error.

Any help appreciated

---

### Post by sdowney717 on 2011-01-06
Grub is great:lolflag:
[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

sudo -i
mount /dev/sda7 /mnt
mount /dev/sda6 /mnt/boot  #skip this one if not have a separate /boot partition
grub-install --root-directory=/mnt/ /dev/sda

mount --bind /proc /mnt/proc
mount --bind /dev /mnt/dev
mount --bind /sys /mnt/sys
chroot /mnt update-grub
umount /mnt/sys
umount /mnt/dev
umount /mnt/proc
exit

grub>find /boot/grub/core.img
grub>root (hdx,y)   (previous command will output the x,y)
grub>kernel /boot/grub/core.img
grub>boot

sudo grub-install /dev/sda

---

### Post by QLee on 2011-01-06
This was not "Locked Out Again" nor "Grub2 Horror" it was all user  action, Windows does as it always does, writes the MBR when it is installed so it can boot.

[QUOTE=Quarkrad]...
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
...[/QUOTE]

At that point you should have stopped, you had rewritten the MBR to boot to the Ubuntu partition. All you did was reinstall Windows, no changes to ubuntu, so no update-grub necessary. However, if you had wanted to run it anyway you could have just rebooted and the GRUB menu would have been what it was before Windows rewrote the MBR.

---

### Post by Quarkrad on 2011-01-06
I'm in again - many thanks :D

---

