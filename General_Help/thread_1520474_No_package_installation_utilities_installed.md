---
title: "No package installation utilities installed"
date: 2010-06-29
forum: General Help
---

### Post by jaufwm on 2010-06-29
I have an internet appliance device that provides a touch screen for users to select various internet functions (something like an oversized iPhone). The unit has a "stripped down" version of what appears to be Ubuntu running on it. The only way to access the Linux environment is through telnet, so no graphical environment.

I would like to install some bluez Bluetooth packages on it, but the device doesn't even have dpkg or apt installed. Also nothing to speak of for development tools to build sources. As an example of the environment, all commands in the bin directories point to a common utility called "busybox", so not an OS meant for general use.

Any suggestions as to how I might get some basic package install utilities and any related dependencies on the system? Unfortunately, the manufacturer of the device doesn't seem to want to offer very much assistance.

The device does have a USB port which allows me to mount a flash drive.

BTW, "uname -a" produces: Linux atom 2.6.24-19-lpia #1 SMP Wed Nov 11 05:10:09 EST 2009 i686 unknown

Thanks for any suggestions.

---

### Post by GreenN00b on 2010-06-29
GCC for example has an install option to install it in a specified folder - see [this link]("http://gcc.gnu.org/install/finalinstall.html").
You can try that on another then copy the folder to the usb and try to use gcc to build new packages on the system.

---

