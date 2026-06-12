---
title: "Changing default OS to Windows 7"
date: 2011-10-19
forum: General Help
---

### Post by Gitominoti on 2011-10-19
Right now I have Windows 7 and Ubuntu 11.10 dual booted with GRUB. Right now Ubuntu is the default OS, but I'd like Windows 7 to be the default. I followed this tutorial to change it, but it didn't work (Ubuntu is still the default).

[http://www.troublefixers.com/set-windows-as-default-booting-os-with-ubuntu-10-04-or-higher-in-dual-boot/](http://www.troublefixers.com/set-windows-as-default-booting-os-with-ubuntu-10-04-or-higher-in-dual-boot/)

The number was 10, and not 0 before I changed it to 4 like the tutorial told me to. I tried using Start-up Manager, but that didn't work either.

Anyone care to help me?

---

### Post by bibble235 on 2011-10-19
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer

Might help you for grub2

Once you install you can open from Applications -> System Toiols -> Grub Customize

[http://www.ubuntugeek.com/grub-customizer-graphical-interface-to-configure-the-grub2burg-settings.html](http://www.ubuntugeek.com/grub-customizer-graphical-interface-to-configure-the-grub2burg-settings.html)

---

### Post by osmak on 2011-10-21
> **Gitominoti said:**
> Right now I have Windows 7 and Ubuntu 11.10 dual booted with GRUB. Right now Ubuntu is the default OS, but I'd like Windows 7 to be the default. I followed this tutorial to change it, but it didn't work (Ubuntu is still the default).

[http://www.troublefixers.com/set-windows-as-default-booting-os-with-ubuntu-10-04-or-higher-in-dual-boot/](http://www.troublefixers.com/set-windows-as-default-booting-os-with-ubuntu-10-04-or-higher-in-dual-boot/)

The number was 10, and not 0 before I changed it to 4 like the tutorial told me to. I tried using Start-up Manager, but that didn't work either.

Anyone care to help me?

The procedure does not say that you need to run update-grub although it is mentioned in the file header. I tried it and it worked for me

---

