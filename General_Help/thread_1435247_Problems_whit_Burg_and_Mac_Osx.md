---
title: "Problems whit Burg and Mac Osx"
date: 2010-03-21
forum: General Help
---

### Post by Jamaicol on 2010-03-21
I've have a problem with the boot of multisystems, I've got Ubuntu 9.1, Windows 7 and Macosx the original in a mac machine (the other post was in my pc for testing), when I install the grub2 of linux ubuntu, mac os X stop booting in a black window.So I modificate the grub.cfg file for mac to boot.
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
    
Is in my macbook pro 2.1 ALL ORIGINAL WINDOWS 7 AND MACOSX LEOPARD and linux ubuntu 9.1

---

### Post by Helkaluin on 2010-03-21
It would be better to modify /etc/grub.d/30_os-prober and run update-grub than to manually modify grub.cfg

EDIT: Disregard that. What a thoughtless reply. Did my research and found that BURG might actually not use grub.cfg, but instead burg.cfg. See the bottom of [https://help.ubuntu.com/community/Burg](https://help.ubuntu.com/community/Burg)

EDIT2: Urgh. You are using burg.cfg after all. I'm such a moron. Continue researching on the matter...

---

### Post by Jamaicol on 2010-03-21
I have done that and grub works perfect but when i install burg doesn't work. 
Even if i modificate the cfg of burg

---

