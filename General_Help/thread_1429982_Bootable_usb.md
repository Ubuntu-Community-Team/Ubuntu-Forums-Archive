---
title: "Bootable usb"
date: 2010-03-14
forum: General Help
---

### Post by boki_thegame on 2010-03-14
Hi to all, 
Can somebody tell me how to make bootable usb drive with edubuntu 9.1??

Thanks a lot

---

### Post by dalee on 2010-03-14
Hi,

[Here]("http://eeebuntu.org/wiki/index.php/Unetbootin") is a link to a step by step guide for creating a bootable USB. They are working with a netbook version, but Unetbootin works for any distro. Just find your .iso and run it. It will create the bootable drive for you. Just make sure you pick the correct target drive!:)

dalee

---

### Post by pastalavista on 2010-03-14
Unetbootin is in the Ubuntu repositories. Use Software Center or Synaptic Package Manager to install it or```
sudo apt-get install unetbootin
```It will appear in the Applications | System Tools menu

---

### Post by wilee-nilee on 2010-03-14
Unetbootin is a good usb loader that can be run in windows or Linux here is another installer.
[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/)

---

### Post by boki_thegame on 2010-03-14
I cant install unetbootin on my edubuntu 7
Here is the error :
Cannot open /home/natka/Desktop/unetbootin-linux-419:No application suitable for automatic installation is avaiable for handling this kind of file.

When im trying with sudo apt-get install unetbootin   in the terminal i have again error. Here is that error: Couldnt find package unetbootin


Thanks a lot

---

### Post by pastalavista on 2010-03-14
> **boki_thegame said:**
> I cant install unetbootin on my edubuntu 7
Here is the error :
Cannot open /home/natka/Desktop/unetbootin-linux-419:No application suitable for automatic installation is avaiable for handling this kind of file.

When im trying with sudo apt-get install unetbootin   in the terminal i have again error. Here is that error: Couldnt find package unetbootin


Thanks a lot

Right-click the icon on the desktop and select Properties--Permissions and make it executable by checking the box. Then you can double-click to open it.

---

### Post by boki_thegame on 2010-03-15
Thank you for all answers. But i have again problem :(

Every time when im booting from usb(made with unetbootin), my eee pc is checking for cd-rom or trying to configure lan network. From where to locate in installation to read files from usb, not from cd-rom?

---

### Post by pastalavista on 2010-03-15
> **boki_thegame said:**
> Thank you for all answers. But i have again problem :(

Every time when im booting from usb(made with unetbootin), my eee pc is checking for cd-rom or trying to configure lan network. From where to locate in installation to read files from usb, not from cd-rom?

You need access the BIOS for that, before grub starts loading. It will usually have the key to press for BIOS setup printed on the first boot screen. On mine, I press F12 and set the motherboard to check USB drive first before HDD or CD/DVD for a boot loader.

---

### Post by boki_thegame on 2010-03-15
Im starting with installation process, but after language setup, it ask me about network and cd-rom?

---

### Post by pastalavista on 2010-03-15
> **boki_thegame said:**
> Im starting with installation process, but after language setup, it ask me about network and cd-rom?

well, maybe you should answer jt haha!

---

