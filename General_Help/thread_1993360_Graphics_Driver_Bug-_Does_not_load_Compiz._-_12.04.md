---
title: "Graphics Driver Bug- Does not load Compiz. - 12.04"
date: 2012-06-02
forum: General Help
---

### Post by bhaveshnande on 2012-06-02
I installed the [Recommended] graphics driver on my Ubuntu 12.04 64-Bit and on reboot I got a black screen with only the cursor movable. On clicking around sometimes I got to see my wallpaper(without any menus or windows), right clicking got me the right click menu, I opened the Settings window through it (through change desktop background > All settings) and then uninstalled my driver)

The Settings window did not had the top part which shows compiz does not start (maybe). Earlier in Ubuntu 11.10 the driver worked pretty well. On asking on #ubuntu IRC they told me to install Ubuntu 11.10 alongside 12.04 or find and install the driver from Nvidia website. 

My Graphics Card: NVIDIA GeForce 6150SE nForce 430.

---

### Post by wildmanne39 on 2012-06-02
Hi, I have the same card and you need the 173 driver but in 12.04 it will not work with xserver so I use the nouveau driver and you have to enable nouveau-firmware.

Compiz and effects work but not as smooth as with the nvidia driver in 11.10.
Thanks

---

### Post by bhaveshnande on 2012-06-02
EDIT: The non [Recommended] driver i.e the second one - (version - current) worked :)

The article here ([https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)) says nouveau driver is the one which you install through the "Additional Drivers".
"By default Ubuntu will use the open source video driver called Nouveau for your NVIDIA graphics card."

---

