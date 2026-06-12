---
title: "start up grub"
date: 2010-07-19
forum: General Help
---

### Post by cowboy7305 on 2010-07-19
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
This is a shot of my start up grub ,do i need all this why cant i just have the window loader and linux image: /boot/vmlinuz-2.6.32-23-generic ,if it can be done how ,and also can i stop it from loading it automatically, 
many thanks

---

### Post by cariboo on 2010-07-20
You can remove the old kernel using System->Administration->Synaptic Package Manager, search for [linux-image[/b], also have a look [here]("https://help.ubuntu.com/community/Grub2") for more info on grub2.

---

### Post by utnubuuser on 2010-07-20
You might also try startupmanager - System>>Administer>>Synaptic Package Manager>>search for startupmanager

and > sudo apt-get update  &&  sudo apt-get autoremoveto remove unneeded software

---

