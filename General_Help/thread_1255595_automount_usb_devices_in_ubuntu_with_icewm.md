---
title: "automount usb devices in ubuntu with icewm"
date: 2009-09-01
forum: General Help
---

### Post by pythonscript on 2009-09-01
How do I set up ubuntu (command line only with icewm as the window manager) to automatically mount devices (usb, cdrom, etc) when I insert them? Thanks!

---

### Post by tgeer43 on 2009-09-01
Doesn't Ubuntu already do this by default?
Mine does anyway - 9.04 64-bit.

Maybe the server edition is different?
Window manager should not make a difference.

tgeer

---

### Post by pythonscript on 2009-09-01
Mine doesn't... I didn't install the server version, per say, though. I installed a command line only version of ubuntu desktop edition, then installed the server kernel manually. That might be all the server version is, but mine detects the hardware, but it doesn't mount it automatically.

---

### Post by tgeer43 on 2009-09-01
Aha! Just found the following at:[COLOR=Blue] _[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)_[/COLOR]
> [SIZE=4][COLOR=Sienna]_Automounting (Ubuntu Server)_[/COLOR][/SIZE][COLOR=Sienna]
By default, disk drives do not automount in Ubuntu Server Edition. If you are looking for a lightweight solution that does not depend on HAL/DBUS, you can install "usbmount".[/COLOR]tgeer

---

### Post by pythonscript on 2009-09-04
Thanks for the tip! I've got that working now with usbmount. Any ideas how I can change usbmount to mount in a directory named, say, the device label? Thanks!

---

