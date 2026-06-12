---
title: "Really need some help with Ubuntu Jaunty 64"
date: 2009-07-07
forum: General Help
---

### Post by Wazz72 on 2009-07-07
I have installed Ubuntu Jaunty 64 on my machine, and really like it.
The machine is a Asus PK5-e Motherboard, 8gb ram, Intel Q6600 Quad Core cpu.  ATI HD2600 PCI-e Video.
All installs well, but If I load the ATI drivers then the machine crashes on reeboot.
So i have re installed several times and left the system running the std 2d drivers.
However after updating and rebooting the system I am just getting a black screen with about an inch of pixels across the top of the screen, and the system freezes.  I cant even CTRl Backspace out of go to a console.
I assume that the system has loaded the wrong video drivers for Gnome.  
How can I fix this without a Re install.  I have tried to repair them from the safe boot option, but it has no effect.
I did read someone else experiencing the same problem, and they fixed it by reducing the color depth or something in a config file.  But I cant find the article.
I could really do with some help.
Thanks 
Warren.

---

### Post by ghostborg on 2009-07-07
Sorry can't help you, but I believe the Crtl-Alt Backspace thing was disabled by default in 9.04 . 

I remember a past version that after an install I had to do updates proir to trying to install any hardware drivers or all hell broke loose.

Good Luck and remember to breathe when you finally had it. haha.

---

### Post by Wazz72 on 2009-07-08
Still need some, help. I still have a messed up gnome login screen.  It must be something to do with one of the updates.  I booted from the live cd and it did the same for a split second, then loaded ok.
also tried:
sudo dpkg-reconfigure -phigh xserver-xorg

look like it copied a file, but made no difference on reboot.
also tried fo fix vga problems from the 2nd boot option menu.

Is there any way of resetting the x server gfx card settings back to degault vga?

really need some help.

thanks.

---

### Post by oomar on 2009-07-08
i have no idea but try booting in recovery mode then get to CLI and use the code 

xconf


idk

---

### Post by Wazz72 on 2009-07-08
Is there no way to recover from a crashed video driver setup?
I want to fix this problem, not have to reinstall the drivers.
Is there any way that I can reset the drivers back to the origonal vga ones.
I did not change them, as I knew the ATI ones were unstable.
Also, whats the best, (Most Stable) Graphics Adapter to use for linux.  I have always used eitre Nvidia or ATI ones.
Whats the best way to Image a partition.  I have set aside a 30 gb partition to put an image of the system on, in case anything like this happens again.
 
Thanks
 
Warren.

---

