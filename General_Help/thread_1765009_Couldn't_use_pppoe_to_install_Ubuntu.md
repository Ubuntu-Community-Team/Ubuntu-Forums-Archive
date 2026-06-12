---
title: "Couldn't use pppoe to install Ubuntu"
date: 2011-05-22
forum: General Help
---

### Post by Ivangelion.tw on 2011-05-22
Hello,

The Ubuntu version I want to install is Server 10.04 LTS 64-bit. My new machine does not have a CD-ROM drive, so I had to install Ubuntu via USB flash drive. 

After following Ubuntu [official website instruction]("http://www.ubuntu.com/download/ubuntu/download") and use "[Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")" to "burn" iso images into USB drive, I could boot Ubuntu via USB smoothly.

However, after going to the installation menu, hitting ESC key twice to enter the command prompt screen, then typing "install modules=ppp-udeb" and going through the installation process, the installer just didn't try to probe my pppoe connection and there is nowhere to set pppoe config. Also my NIC cable had already connected to the pppoe device. 

Is there anything wrong with my set up? 

Any help will be greatly appreciated.

---

### Post by dcstar on 2011-05-23
> **Ivangelion.tw said:**
> Hello,

The Ubuntu version I want to install is Server 10.04 LTS 64-bit. My new machine does not have a CD-ROM drive, so I had to install Ubuntu via USB flash drive. 

After following Ubuntu [official website instruction]("http://www.ubuntu.com/download/ubuntu/download") and use "[Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")" to "burn" iso images into USB drive, I could boot Ubuntu via USB smoothly.
........

You do **not** need to use "pppoe" to do any Ubuntu installation, just install it normally and do any "pppoe" configuration **after** installation.

---

### Post by Ivangelion.tw on 2011-05-23
> **dcstar said:**
> You do **not** need to use "pppoe" to do any Ubuntu installation, just install it normally and do any "pppoe" configuration **after** installation.

However, when I passed the network configuration part, I could not install Ubuntu at all! And I only got "installer" in USB, i.e. there is only "Ubuntu Server 10.04.x amd64 Installer" option in Universal USB Installer, no "full files" option.

---

### Post by Ivangelion.tw on 2011-05-24
Anyone?

---

