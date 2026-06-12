---
title: "GRUB2 and GRUB aren't playing nicely."
date: 2011-04-10
forum: General Help
---

### Post by sirspazzolot on 2011-04-10
Trying to dualboot Ubuntu 11.04 and Backtrack 4 rc2. Booting Backtrack with GRUB2 gives ```
error: zImage doesn't support 32-bit boot (try with 'linux16').
```
Trying to boot Ubuntu with GRUB gives something like Error 15: File not found. I have tried having GRUB2 in the MBR and GRUB installed in the backtrack root partition and vice versa. I guess I don't know how to chainload. Could somebody explain how I would go about getting GRUB2 in the MBR to chainload to GRUB installed in /dev/sda7? If that definitely won't work, then I might install that plop boot manager to the MBR and try to get that to load grub(2) which would be installed in the root partition of its respective distro.

Thanks in advance.

---

### Post by Dutch70 on 2011-04-10
I don't know if this will be of much help, but I have several distro's that use Grub2, and then there's PCLinuxOS. :)

In order to get it to boot from Grub2, I have to change one number in grub.cfg...
```
menuentry "PCLinuxOS-10.12 (on /dev/sda6)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 3f399271-92e3-4683-827d-45125fea0d8c
	linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=3f399271-92e3-4683-827d-45125fea0d8c resume=UUID=8316ec3c-6153-427c-bb21-884dc8b29de6 splash=silent vga=788
	initrd [COLOR="Red"](hd0,5)[/COLOR]/boot/initrd.img
```

I change (hd0,5) to (hd0,6) and it boots fine. Then, when you updat-grub, it goes back.
There is a way to make this permanent, but I'm not sure what it is. I know that doesn't solve your problem, 
but hopefully it will help you come to a solution.

Edit: After reading your post again, I'm not sure this has anything to do with your problem. I'll leave it anyway, just in case.

---

### Post by sirspazzolot on 2011-04-10
Lol alright, thanks. I think I'll try deleting all the partitions and reinstalling, backtrack first then Ubuntu, and if that won't work, I'll just stick with Ubuntu.

---

### Post by Dutch70 on 2011-04-10
Before you do that, post your grub.cfg from Ubuntu please.

```
sudo gedit /boot/grub/grub.cfg
```

---

