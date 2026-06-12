---
title: "ubuntu 9.10 usb boot - no hard drive"
date: 2010-05-17
forum: General Help
---

### Post by Tekken on 2010-05-17
Hello,

I want to automatically boot from a USB flash drive on a system with no hard drive. I have tried this already and I am sent to a menu that has:

Install Ubuntu Server
Install Ubuntu Enterprise Clo
Check disc for defects
Test Memory
Boot from first hard disk
Advanced options
Help

The first 2 will do nothing when selected except reset the timer (starting at 30s ) at the bottom of the screen.
Help has a menu with different topics. When I try to boot I get : Could not find kernel image: /install/vmlinuz

I'm not sure why this would happen. I used the same ISO that I used to install Ubuntu on other systems ( with a hard drive ). I was also using a CD to install the OS. 

I believe I used "universal-USB-installer-v1.5.5.exe" to write the ISO to the flash drive.

Is there a step that I missed? Do I need a different distro to do this on a flash drive?

I had looked at several topics and with a similar problem people were having others were mentioning the syslinux.cfg was messed up.
The syslinux.cfg file I have is as follows:

include menu.cfg
default vesamenu.c32
prompt 0
timeout 300
gfxboot bootlogo


I don't know if that helps, but please let me know if there is something I did wrong, or if there is something I can read to solve my problem. 

Thanks!

---

### Post by Tekken on 2010-05-19
I still have gotten no reply. If this issue has been addressed previously please let me know. If there is any other information that I can give please let me know.

Thanks

---

### Post by snowpine on 2010-05-19
What I would do is this: Boot the Ubuntu CD on a computer with no hard drives connected. Insert the USB stick. Use the "regular" installer to do a full install to the USB stick, as though you were installing to a hard drive.

This will do a "full install" rather than the unsupported "universal-usb-installer" method (I don't even know what that is!) In other words, you will have a totally normal Ubuntu install, except that the "hard drive" is your USB stick rather than internal to the computer. Hope that makes sense.

ps If you have enough RAM and you are concerned about the lifespan of your flash drive (I'm not; they're cheap these days) you might consider choosing Manual Partitioning and *not* using a swap partition.

---

### Post by Darkness Des on 2010-05-19
What Snowpine said will work just fine. In the future, try using Ubuntu to create the startup disk. In 9.10 System -> Administration -> USB Startup Disk Creator. I find that those always work fine, as I lack a CD burner and use Flash Drives instead.

---

### Post by Tekken on 2010-05-20
Thanks guys, this worked great.

---

