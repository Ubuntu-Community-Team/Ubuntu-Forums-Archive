---
title: "changing grub menu.lst"
date: 2006-06-18
forum: General Help
---

### Post by oldmanstan on 2006-06-18
I've never really messed with grub other than to take out the old menu items after kernel upgrades but I decided to put vector linux on my other hard drive (which used to be for windows but has since been liberated). I wanted to add it to grub and i think i got it setup properly but i'm not positive.

if i got something wrong and i try to boot to the other hard drive can i screw anything up permanently? or will it just fail to boot?

---

### Post by taurus on 2006-06-18
It will just fail to boot, if the entry for Vector Linux is wrong.  If you want, you can post your /boot/grub/menu.lst and the output of "fdisk -l" and people will have a look for you...

---

### Post by oldmanstan on 2006-06-18
Awesome!

here's the fdisk -l output...

```
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4416    35471488+  83  Linux
/dev/hda2            4679        4865     1502077+   5  Extended
/dev/hda5            4679        4865     1502046   82  Linux swap / Solaris

Disk /dev/hdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9777    78533721   83  Linux
/dev/hdc2            9778        9964     1502077+   5  Extended
/dev/hdc5            9778        9964     1502046   82  Linux swap / Solaris
```

and here's the menu.lst entry i made
```

# linux installation on /dev/hda1.
title		Vector Linux, kernel 2.6.13 (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.13 root=/dev/hda1 ro quiet splash 
initrd		/boot/initrd
savedefault
boot
```

thanks a bunch!

---

### Post by mlind on 2006-06-18
You should probably use grub-install script if you want to put grub on another hdd.
update-grub if you just want to update references.

You should not modify actual kernel boot configuration, but the root,groot
parameters on menu.lst and then run update-grub.

---

### Post by oldmanstan on 2006-06-18
ok, so when i run grub-install do i need to specify the root-directory option? if so, what do i put there? the root for the other HD or the /boot folder?

---

### Post by mlind on 2006-06-18
[QUOTE=oldmanstan]ok, so when i run grub-install do i need to specify the root-directory option? if so, what do i put there? the root for the other HD or the /boot folder?[/QUOTE]

You need to specify the install device, which means actual HDD (not partition).
Like /dev/hda or /dev/sda. This will install GRUB on that's harddrives MBR.
You should have /boot mounted before doing so, so that correct stuff is written
there too.

---

