---
title: "No Splash Screen in Lucid!"
date: 2010-05-23
forum: General Help
---

### Post by Fixman on 2010-05-23
I recently installed from scratch the Lucid Lynx, and after changing the direction of the window buttons and a few things more (**who was the idiot who thought on having a purple terminal?**), I completely loved it.

I had one problem through, is that when I boot my computer, there is no splash shown. After the GRUB menu, all I see is a black terminal with no text for some time, and then a quick view of some colored text. Does anyone else have this problem? Here is the appropriate section of the grub.cfg file:

```
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,3)'
	search --no-floppy --fs-uuid --set d94e32b7-e4b4-4c80-b627-e093d6be63a8
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=d94e32b7-e4b4-4c80-b627-e093d6be63a8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
```

I have a built-in Intel Graphic card.

---

### Post by TeoBigusGeekus on 2010-05-23
[See the Bootup/Plymouth section]("http://ubuntuforums.org/showthread.php?t=1469475")

---

