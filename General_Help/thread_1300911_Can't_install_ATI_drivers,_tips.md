---
title: "Can't install ATI drivers, tips?"
date: 2009-10-25
forum: General Help
---

### Post by munkifisht on 2009-10-25
I am having real trouble getting the ATI drivers to run correctly. I am running 9.10 and the drivers are for a HD 4800.

In Hardware devices, the proprietary drivers are available to download. When I do download them they seem to install fine, or at least, they download fine. Then when I reboot, the screen flickers a few times, then goes black. The system does not stall and I am able to ctrl+alt+2 to the command line. This allows me to uninstall the old drivers and reinstall the generics. Rebooting I then can boot to the safe graphics mode before the generic drivers kick in and it's back to square one.

Any help or direction on what to do here would be great. Thanks

---

### Post by P4man on 2009-10-25
I bet the drivers work fine but its setting a resolution your monitor cant handle. Try running xrandr to change it, and then ctrl+alt+F7 to get back to the gui. Have a look here:

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by munkifisht on 2009-10-25
> **P4man said:**
> I bet the drivers work fine but its setting a resolution your monitor cant handle. Try running xrandr to change it, and then ctrl+alt+F7 to get back to the gui. Have a look here:

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Doesn't seem to work. When I try to run it from the command line I get an error "Can't open display"

Also, the screen is detected under the propority drivers correctly. It's linked via DVI and the system recognises the screen make and settings automatically.

---

### Post by P4man on 2009-10-25
edit: nevermind not correct

---

### Post by munkifisht on 2009-10-26
Bump

---

### Post by phillw on 2009-10-26
Hi,

There's a live thread on ATI drivers here ....

[http://ubuntuforums.org/showthread.php?t=1238129&highlight=ati+driver](http://ubuntuforums.org/showthread.php?t=1238129&highlight=ati+driver)

Regards,

Phill.

---

