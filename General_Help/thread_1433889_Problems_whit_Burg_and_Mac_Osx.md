---
title: "Problems whit Burg and Mac Osx"
date: 2010-03-19
forum: General Help
---

### Post by Jamaicol on 2010-03-19
I've have a problem with the boot of multisystems, I've got Ubuntu 9.1, Windows 7 and Iatkos v7 (macosx), when I install the grub2 of linux ubuntu, mac os X stop booting in a black window.So I modificate the grub.cfg file for mac to boot.
Change /boot/grub/grub.cfg menuentry of mac like that;

menuentry "MacOS X" {
insmod hfsplus
set root=(hd0,2)
multiboot /boot
}
With this grub2 make boot perfect Macosx but when I install burg with sora_clean theme it creates me 2 entryes of mac and neither of them work. I have tried to copy the same code to /boot/burg/burg.cfg like 

menuentry "MacOS X" {
insmod hfsplus
set root='(hd0,2)'
multiboot /boot
}
But os couse doesn't work.
Does anyone know how to make boot macosx in burg?

Thanks

---

### Post by zvacet on 2010-03-20
Do you really think you will get support for pirated software here?Ask somewhere else,please!

---

### Post by cariboo on 2010-03-20
We don't condone illegal activities here, this thread is closed.

---

