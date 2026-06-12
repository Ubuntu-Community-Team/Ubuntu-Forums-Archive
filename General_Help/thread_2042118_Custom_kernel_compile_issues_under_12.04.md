---
title: "Custom kernel compile issues under 12.04"
date: 2012-08-14
forum: General Help
---

### Post by Raptor354 on 2012-08-14
I'm trying to compile my own kernel (3.5) under Ubuntu 12.04.

What I did:
After copying over the config from the existing kernel (one from the repos) and merging the new options (using the defaults), I build a deb.  I then install the deb as one usually installs a deb.

Symptoms:
When the desktop environment loads, I discover I cannot access USB devices.  A PS/2-based keyboard works fine, which I can use when I drop into a new tty or open a terminal window.  X does not report any USB input devices.

Possible causes:
Perhaps the modules didn't get compiled into the kernel before the install.

Other (questionably relevant) information:
If I boot into an older kernel, everything works beautifully.
It appears as though it does see the various USB hubs, probably located in the motherboard.

Is there a a place I can check whether or not everything I need gets loaded?  Or does somebody see what my problem is right off?  Logs are available upon request.

---

### Post by demikid on 2012-09-13
I have the same problem. After following [this]("http://mitchtech.net/compile-linux-kernel-on-ubuntu-12-04-lts-detailed/") guide with 3.5.3 Kernel,  usb devices (wireless mouse, usb-serial converter etc) are not being recognized.

---

### Post by Bobhuber on 2012-09-13
Don't use the localmod config option unless you know what you are doing with make menuconfig and know which options to add.

---

