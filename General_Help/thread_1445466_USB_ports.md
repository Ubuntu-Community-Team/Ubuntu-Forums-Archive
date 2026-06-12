---
title: "USB ports"
date: 2010-04-02
forum: General Help
---

### Post by e24ohm on 2010-04-02
Folks:
What are the cli to find the usb ports that are being used on my machine, or the location of the port.

I know that /dev/tty# are teh serial ports, but what about the usb ports?

I have trying to configure minicom for usb serial adapter.

thanks.

---

### Post by burton247 on 2010-04-02
not 100% sure exactly what your after but lsusb can be used for information about usb ports and the devices attached.

[http://linuxcommand.org/man_pages/lsusb8.html]("http://linuxcommand.org/man_pages/lsusb8.html")

there's the options you can use with it

---

### Post by e24ohm on 2010-04-02
> **burton247 said:**
> not 100% sure exactly what your after but lsusb can be used for information about usb ports and the devices attached.

[http://linuxcommand.org/man_pages/lsusb8.html]("http://linuxcommand.org/man_pages/lsusb8.html")

there's the options you can use with ithey this is a neat little command. Thanks; however, what is the default port name? like Serial ports are ttyS#, but what is the format for USB ports.

---

### Post by kambrik on 2010-04-02
Im pretty sure its usbmon0, usbmon1, ...

---

### Post by e24ohm on 2010-04-03
> **kambrik said:**
> Im pretty sure its usbmon0, usbmon1, ...Folks: Just wanted to do a follow up on this thread. On 8.04, the USB port is showing up as [FONT="Courier New"]**/dev/ttyUSB0**[/FONT].

Thanks for the help.

---

