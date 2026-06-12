---
title: "windows 7 grub boot code error"
date: 2011-12-20
forum: General Help
---

### Post by jerguy1928 on 2011-12-20
Hi i have ubuntu 11.04 and when i switched from wubi to a partition the windows 7 boot code for grub got corrupted (according to my friend who is a paid computer technician. the current code is this:```
insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root BA2A08D42A088F95
	chainloader +1
}
```
could someone advise what it should be?
thanks.

---

### Post by Synoc on 2011-12-20
Wubi points the boot loader to a file on the windows partition, if you installed ubuntu on another partition you might simply need to point grub there, but editing grub2 is well beyond me, they did not make it easy.

---

### Post by yetiman64 on 2011-12-20
> **Synoc said:**
> Wubi points the boot loader to a file on the windows partition, if you installed ubuntu on another partition you might simply need to point grub there, but editing grub2 is well beyond me, they did not make it easy.
Running```
sudo update-grub
```from the Ubuntu install should fix that. When running this command os-prober is also run, this should alter the Windows entry in grub.

Have you tried the update-grub command yet OP ? Maybe worth a try if you haven't already.

---

### Post by bcbc on 2011-12-20
> **jerguy1928 said:**
> Hi i have ubuntu 11.04 and when i switched from wubi to a partition the windows 7 boot code for grub got corrupted (according to my friend who is a paid computer technician. the current code is this:```
insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root BA2A08D42A088F95
	chainloader +1
}
```
could someone advise what it should be?
thanks.

Mine looks similar:
```
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
        insmod part_msdos
        insmod ntfs
        set root='(hd0,msdos2)'
        search --no-floppy --fs-uuid --set=root CAB28E67B28E5839
        chainloader +1
}

```
There is a difference in that mine refers to /dev/sda2 as (hd0,msdos2) and yours as (/dev/sda,msdos2) but that's probably just a different grub version. They should have the same effect.
You can check the UUID by running:
```
sudo blkid
```

Also, check the partition with the boot flag set by running:
```
sudo fdisk -l
```
The partition with the boot flag is the one you need to boot Windows. Sometimes grub confuses the recovery partition with the boot partition. So choose the one with the boot flag.

---

