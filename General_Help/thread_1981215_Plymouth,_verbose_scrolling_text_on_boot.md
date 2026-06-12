---
title: "Plymouth, verbose scrolling text on boot"
date: 2012-05-16
forum: General Help
---

### Post by technocp on 2012-05-16
Did you manage to get scrolling messages in plymouth.

I am trying it but with no success.

I have managed to display one line text. but plymouth update --status=<string> option doesn't work for me

any ideas....

---

### Post by Zvlwab on 2012-05-16
A menuentry in /boot/grub/grub.cfg looks like this:
```
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root fadc3ccb-e2c6-4695-a55c-58326bc4fb53
	linux	/boot/vmlinuz-3.2.0-24-generic root=UUID=fadc3ccb-e2c6-4695-a55c-58326bc4fb53 ro   radeon.audio=1
	initrd	/boot/initrd.img-3.2.0-24-generic
}

```
where $linux_gfx_mode is either keep or text.

Usually $linux_gfx_mode has the value keep, which will fix your tty resolution.
You can change $linux_gfx_mode to text. This will give the verbose output you want, but then the boot screen and tty both have an ugly resolution.

As far as I know it's not possible to get a verbose output with a nice resolution since Ubuntu 11.04.

---

### Post by oldos2er on 2012-05-16
Posts moved to their own thread.

---

