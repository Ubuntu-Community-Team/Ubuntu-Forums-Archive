---
title: "Brightness control"
date: 2011-09-28
forum: General Help
---

### Post by Stratos560 on 2011-09-28
Firstly, I am a complete noob to Ubuntu and Linux. I have an Acer Aspire 5750 with an i3-2310m and intel HD graphics 3000. I have spent the good part of an hour trying to find out how to adjust the brightness of my screen. Both the power management and fn key do nothing. Can someone please help!!! Oh and i'm using 11.04. Thanks!!

---

### Post by rusty725 on 2011-09-29
sudo gedit /etc/default/grub
Change the line *GRUB_CMDLINE_LINUX=""* into
GRUB_CMDLINE_LINUX="acpi_osi=Linux"
sudo update-grub

[http://ubuntuforums.org/showpost.php?p=9291657&postcount=1](http://ubuntuforums.org/showpost.php?p=9291657&postcount=1)

---

### Post by HermanAB on 2011-09-29
xbacklight

---

