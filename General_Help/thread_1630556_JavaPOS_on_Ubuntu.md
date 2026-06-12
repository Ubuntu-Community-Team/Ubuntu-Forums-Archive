---
title: "JavaPOS on Ubuntu"
date: 2010-11-25
forum: General Help
---

### Post by agalvao on 2010-11-25
I'm trying to create an image using Ubuntu as the OS for a Retail store Register system.
the Hardware is IBM 4800-743 registers, 4610TG4 printers and POS keyboards, the actual application is a Java application. I have the POS application, Database and Tomcat all configured and running, my last and only real issue is the peripherals more directly the JPOS peripheral ie. 4610 printer, these require JPOS drivers I have IBM  jposl171ga for Linux but when I rub the setup I get the message stating that I need to be root to install or un install jpos. I have used sudo and actually su to root but still get the same message, I have even enabled root login and logged in as root still the same. 
Can anyone help with this issue, this would be a large deployment if I can get this last issue resolved. We are currently using SLES as the OS but are having lots of issues with KDE I want to move to Ubuntu as I believe it to be more stable. Any input is appreciated.

---

### Post by searchfgold6789 on 2010-11-25
Knowing the exact error message you got would probably help, because we need to know if the installer script needs to be run as root, and the installer tries to determine it, or if sudo is not working.
Could you post what you type into the terminal and what the output is?

---

