---
title: "Adjust LCD Monitir Brightness Jaunty"
date: 2009-09-10
forum: General Help
---

### Post by elnegrito on 2009-09-10
Any idea on how to adjust the LCD monitor brightness in Ubuntu 9.4 (Jaunty)?

It used to be (on Ubuntu 8.4) as easy as typing "echo -n 00 > /proc/acpi/video/VGA/LCD/brightness" in a terminal. Where 00 was the desired value. I used to use 86 as the value of choice. Using this setting was the only way to get the photos that I edited with The Gimp or any other image editor to appear as bright as on my screen.

Unfortunately on Jaunty the "/proc/acpi/video" folder is empty and the command returns an error.

I also tried following the instructions on [this post]("http://ubuntuforums.org/showthread.php?p=4168042#post4168042"), but that didn't work ether.

I understand that the "prints to dark" situation is quite common when using LCD monitors but I do a fear amount of image editing and the earlier mentioned code worked just perfect for me. It makes no difference if I printed the images at home or at those one hour photo printers. The difference in color/brightness was, at least for me, unnoticeable.

Any Ideas? At least whats the "/proc/acpi/video/VGA/LCD/brightness" equivalent in Jaunty?

My system is a desktop (not a notebook) with an MSI Socket AM2+ Motherboard (AMD 790X (ATI RD780) Chipset & ATI SB600 Chipset) AMD 3GHz dual core CPU (Athlon 64 X2 6000+), 4GB ram an ATI Radeon graphics card (256 GB) and Dell 17" LCD Monitor.

Any help much appreciated!

---

### Post by Baneblade on 2009-09-10
> **elnegrito said:**
> Any idea on how to adjust the LCD monitor brightness in Ubuntu 9.4 (Jaunty)?

It used to be (on Ubuntu 8.4) as easy as typing "echo -n 00 > /proc/acpi/video/VGA/LCD/brightness" in a terminal. Where 00 was the desired value. I used to use 86 as the value of choice. Using this setting was the only way to get the photos that I edited with The Gimp or any other image editor to appear as bright as on my screen.

Unfortunately on Jaunty the "/proc/acpi/video" folder is empty and the command returns an error.

I also tried following the instructions on [this post]("http://ubuntuforums.org/showthread.php?p=4168042#post4168042"), but that didn't work ether.

I understand that the "prints to dark" situation is quite common when using LCD monitors but I do a fear amount of image editing and the earlier mentioned code worked just perfect for me. It makes no difference if I printed the images at home or at those one hour photo printers. The difference in color/brightness was, at least for me, unnoticeable.

Any Ideas? At least whats the "/proc/acpi/video/VGA/LCD/brightness" equivalent in Jaunty?

My system is a desktop (not a notebook) with an MSI Socket AM2+ Motherboard (AMD 790X (ATI RD780) Chipset & ATI SB600 Chipset) AMD 3GHz dual core CPU (Athlon 64 X2 6000+), 4GB ram an ATI Radeon graphics card (256 GB) and Dell 17" LCD Monitor.

Any help much appreciated!

You can add an applet to your bar by right-clicking it, choosing "Add to Panel" and then picking the "Brightness Applet".

---

### Post by elnegrito on 2009-09-10
Actually the brightness applets lowest setting is still too bright.

---

