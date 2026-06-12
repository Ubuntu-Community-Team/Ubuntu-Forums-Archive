---
title: "Grub 2 and static kernel"
date: 2010-03-30
forum: General Help
---

### Post by Arch Linux on 2010-03-30
Because Grub2 wants to automate the grub config creation, it also pulls the "initrd" line with my Arch Linux entry.

But the thing is that my kernel is static so I don't want to have the line there but neither do I want to delete it every time I run "grub-mkconfig -o /boot/grub/grub.cfg".

I also don't want to have 3 entries for my kernel, when 2 is enough.

Clarification:
```
menuentry "Arch Linux, with Linux vmlinuz26-ice" --class archlinux --class gnu-linux --class gnu --class os {
	set gfxpayload=keep
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 88cb8273-2744-4ce5-876d-d46d48c860c7
	echo	Loading Linux vmlinuz26-ice ...
	linux	/boot/vmlinuz26-ice root=/dev/sda1 ro  logo.nologo quiet console=tty1 splash=silent,theme:arch-glass,fadein,fadeout
[B]	echo	Loading initial ramdisk ...
	initrd	/boot/kernel26-ice.img[/B]
}

[COLOR="Red"]**I do not need this line:**[/COLOR]
[COLOR="Red"]**---------------------------------------------------------------**[/COLOR]
[I]menuentry "Arch Linux, with Linux vmlinuz26-ice Fallback" --class archlinux --class gnu-linux --class gnu --class os {
	set gfxpayload=keep
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 88cb8273-2744-4ce5-876d-d46d48c860c7
	echo	Loading Linux vmlinuz26-ice ...Loading Linux Fallback ...
	linux	/boot/vmlinuz26-ice root=/dev/sda1 ro  logo.nologo quiet console=tty1 splash=silent,theme:arch-glass,fadein,fadeout
[B]	echo	Loading initial ramdisk ...
	initrd	/boot/kernel26-ice-fallback.img
}[/B][/I]
[COLOR="Red"]**---------------------------------------------------------------**[/COLOR]

menuentry "Arch Linux, with Linux vmlinuz26-ice Fallback (recovery mode)" --class archlinux --class gnu-linux --class gnu --class os {
	set gfxpayload=keep
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 88cb8273-2744-4ce5-876d-d46d48c860c7
	echo	Loading Linux vmlinuz26-ice ...Loading Linux Fallback ...
	linux	/boot/vmlinuz26-ice root=/dev/sda1 ro single
[B]	echo	Loading initial ramdisk ...
	initrd	/boot/kernel26-ice-fallback.img[/B]
}
```

---

### Post by oldfred on 2010-03-30
I modified my grub. I limited Ubuntu lines to two. Turned off prober so it does not look for other systems and created my own 40_custom. 

includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)

gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER="true"

Another way:
Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

---

### Post by Arch Linux on 2010-03-31
Hey, that's a superb guide. Thanks, will check it out. 

I'll mark this as [Solved] later on so if anybody wants to add something, now is the time to do so =).

---

