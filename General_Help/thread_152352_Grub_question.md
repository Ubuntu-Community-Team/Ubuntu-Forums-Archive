---
title: "Grub question"
date: 2006-03-29
forum: General Help
---

### Post by Minn3h on 2006-03-29
I had GRUB installed before.  Did some things which over-wrote it.  Used my Ubuntu live cd to go into grub and:
root (hd1,0)
setup (hd1,0)
But now, when my computer goes to boot, I just get "GRUB _" with the cursor flashing.

from menu.lst:
title		Ubuntu, kernel 2.6.12-10-amd64-generic Default 
root		(hd1,0)
kernel		/boot/vmlinuz root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img
savedefault
boot

Ideas?

---

### Post by ispmarin on 2006-03-29
did you try to boot from the live cd, mount your partition, do a chroot on the partition you have mounted, and done a grub-install?

---

### Post by Minn3h on 2006-03-29
[QUOTE=ispmarin]did you try to boot from the live cd, mount your partition, do a chroot on the partition you have mounted, and done a grub-install?[/QUOTE]

I'm not familiar enough with those commands to confidently do it myself.  Can anyone help me with those?

---

### Post by ispmarin on 2006-03-29
Ok, I will try. Boot from the live cd, and waits for the boot to finish. Then open a terminal and type 
sudo su
Be careful! Now you are working as root, so you can damage your system. I suppose that the partition with ubuntu is /dev/hdb1, so I will use it. If not, you will have to look on the dmesg output
dmesg
and look for something like hda, hdb, or sda and sdb, if it is a serial ata hd. When you have the right partition, issue
mount /dev/hdb1 /mnt
and you old filesystem should be mounted on /mnt. Try then 
chroot /mnt
and the root system now is you old filesystem. Then you can try to do 
grub-install
and sees grub reinstalling the boot sector. Warning: if you have a windows partition, it is not garanteed that grub will put it on boot (you windows installation will be trashed)! This is what I can remember, so be careful... :mrgreen: 
Hope it helps.

---

### Post by Minn3h on 2006-03-29
I'd like it to install the boot sector to hdb1 not the MBR, is this possible in grub-install? Or does it just do whatever it wants?

EDIT: Nevermind, it seems if i do "grub-install /dev/hdb1" it will do what i want.

---

### Post by Minn3h on 2006-03-29
Well, I did:
sudo mount -t ext3 /dev/hdb1 /mnt
sudo chroot /mnt
sudo grub-install /dev/hdb1

And I still have the same problem, still "GRUB _" when I boot.

---

