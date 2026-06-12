---
title: "Manually configure X11"
date: 2006-04-28
forum: General Help
---

### Post by wyo on 2006-04-28
I've just installed Ubuntu 5.10 on a A8N-VM motherboard (nForce4 chipset) with an integrated Nvidia 6150 graphic which isn't correctly detected by the hardware detection.

1) Is there a x11 driver for this graphic?

2) Is there a frame buffer driver?

3) Where does Ubuntu store the X11 configuration?

O. Wyss

---

### Post by echo $USER on 2006-04-28
1. maybe [this]("http://easylinux.info/wiki/Ubuntu#How_to_install_Graphics_Driver_.28NVIDIA.29")?

2. I don't know, anyone else?

3. /etc/X11/xorg.conf  but do not muck with it until you back it up.

---

### Post by wyo on 2006-04-29
[QUOTE=echo $USER]
1. maybe [this]("http://easylinux.info/wiki/Ubuntu#How_to_install_Graphics_Driver_.28NVIDIA.29")?
[/QUOTE]

Thanks, might work, albeit I can't check it now since my network isn't working.

[QUOTE=echo $USER]
2. I don't know, anyone else?
[/QUOTE]

Isn't there a pci-info utility which gives more infos about the card? Does anybody know its correct name?

[QUOTE=echo $USER]
3. /etc/X11/xorg.conf  but do not muck with it until you back it up.
[/QUOTE]

Thanks.

The console mode in Ubuntu really sucks, for a newbie it's impossible to work with. The keybord seems to be okay but the display just shows English characters. Besides the bash shell bells all over the place, can't the sound be disable by default?

O. Wyss

---

