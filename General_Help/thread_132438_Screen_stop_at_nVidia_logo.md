---
title: "Screen stop at nVidia logo"
date: 2006-02-18
forum: General Help
---

### Post by xphp on 2006-02-18
I have installed nvidia driver for my TNT2 card, but I get wrong setting in xorg.conf and then it stop at nVidia logo and can not be kill (pressing CTRL+ALT+BACKSPACE and CTRL+ALT+Fx)

I need to edit xorg.conf, how can I stop loading gdm on startup!

Thank you

---

### Post by Gustav on 2006-02-18
Newer drivers doesn't suppord old cards as yours, use the old driver (the nvidia-legacy package)

---

### Post by xphp on 2006-02-18
I use legacy driver, it used to run fine before but since I add
  Option "NoRenderExtension" "true"
it stop at nVidia logo

How can I stop loading gdm at startup? is there a keyboard shortcut to stop it?

---

### Post by SWAT on 2006-02-18
[QUOTE=xphp]I use legacy driver, it used to run fine before but since I add
  Option "NoRenderExtension" "true"
it stop at nVidia logo[/QUOTE]Isn't the solution obvious? Just edit the line to what it was before and you should be fine :P

I don't know if the newer drivers support your old card, I really don't. But I used [this howto ](http://www.zwhlug.nl/content/nvidia_nvidia_driver_1_0_8178_installation_on_ubuntu_breezy_5_10)for installing the nvidia drivers for my *new* 6600GT, maybe it will help you?

---

### Post by xphp on 2006-02-22
Thank for every comments, now I can edit xorg.conf by use a live cd and mount the disk then login as root and so on! :D

---

### Post by Jason_25 on 2006-02-22
You do know about virtual terminals and the recovery mode right?  There should be no reason to use a live cd just to edit the xorg file, even if gdm doesn't start.

---

