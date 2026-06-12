---
title: "Multiple Kernels showing up in GRUB 1.98 menu"
date: 2011-06-23
forum: General Help
---

### Post by DJGCrusader on 2011-06-23
So after running into multiple mid-installation errors trying to install 11.04 on my Thinkpad, I decided I didn't really want Unity anyway, so I installed 10.04 without a trace. Now I'm trying to custimize my Grub menu, and notice there are the following entries:

```
### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 581f0734-d3d8-4e9a-aad5-2045fe55536d
	linux	/boot/vmlinuz-2.6.32-32-generic root=UUID=581f0734-d3d8-4e9a-aad5-2045fe55536d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 581f0734-d3d8-4e9a-aad5-2045fe55536d
	echo	'Loading Linux 2.6.32-32-generic ...'
	linux	/boot/vmlinuz-2.6.32-32-generic root=UUID=581f0734-d3d8-4e9a-aad5-2045fe55536d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 581f0734-d3d8-4e9a-aad5-2045fe55536d
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=581f0734-d3d8-4e9a-aad5-2045fe55536d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 581f0734-d3d8-4e9a-aad5-2045fe55536d
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=581f0734-d3d8-4e9a-aad5-2045fe55536d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 581f0734-d3d8-4e9a-aad5-2045fe55536d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 581f0734-d3d8-4e9a-aad5-2045fe55536d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Mode" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 32BCADF2BCADB0B1
	chainloader +1
}
menuentry "Windows 7" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 286290C762909AE0
	drivemap -s (hd0) ${root}
	chainloader +1
```

Note: I changed the names of the Windows Recovery Mode (Grub thought it was Vista) and Windows 7 (Grub thought it was the Vista Recovery Mode). 

So, why does it list Ubuntu, with Linux 2.6.32-32-generic and its recovery mode along with Ubuntu, with Linux 2.6.32-28-generic and its recovery mode. 

32 vs 28? What does this number mean? I've looked around and I think it means the kernel Ubuntu's using. So why the different options? Is this left over from when i tried to install Natty? 

When I boot into each I can't tell any difference, each option (not the recovery modes) boots into the same 10.04 installation. 
So can I just remove the 28 one and it's recovery entry? Also, Can I change the order so Ubuntu and Win7 are at the top, then their recovery modes and that memtest  stuff are at the bottom? (I've read up on the differences between the old Grub and 1.98, and nowhere in the new Grub's documentation can I find whether or not I can change the order of the menu, only the option to change which entry is default). I just don't want another bootloader crisis on my hands, I've had enough of those.

Thanks.

---

### Post by LordNeo on 2011-06-23
First of all, you should use "update-grub" to get a freshly generated grub menu.
Despite of that, all those info are generated from the "update-grub" command and is not intended to be manually changed (you can change the files in /etc/grub.d/ instead), so you can see why it was detected wrongly (if once updated it still display the same info).

In order to change the display order you can just rename the files (10_linux -> 50_linux) and it will change the order.

---

### Post by gizmo720 on 2011-06-23
This means that you have 2 kernels in your /boot directory. This is probably a result of installing 11.04 first, but also happens when a new kernel is released in the updates. Either one will work, but if you really only want one of them, you can delete the older kernel from /boot, then run sudo update-grub.

---

### Post by TeoBigusGeekus on 2011-06-23
They are just the different linux kernels you got from updating your system.
It is generally advised to keep the latest + one before it.
If the latest kernel screws your system, you can always boot with the previous one.
If you want to remove old kernels, open Synaptic and search for linux-image.
Right click the ones you don't want and select completely remove.
After that, do a 
```
sudo update-grub
```
and you're done.

---

### Post by TeoBigusGeekus on 2011-06-23
> **gizmo720 said:**
> This is probably a result of installing 11.04 first...
Nope. Natty uses a much later kernel than 2.6.32.

---

