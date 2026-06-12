---
title: "USB ports inop w/2.6.32-33"
date: 2011-09-06
forum: General Help
---

### Post by Barney on 2011-09-06
USB ports went inop with kernel 2.6.32-33 ???  All worked normally before.

usbmount installed/uninstalled, no difference.

Any help?

---

### Post by Barney on 2011-09-09
Much searching produced this fix: I used synaptic to install usb-modeswitch and usb-modeswitch-data. During the installation, synaptic requested that the 10.04.3 LiveCD be inserted - I did that, and the installation continued. After the installation, rather than reboot, I shutdown, removing the LiveCD while power was still on. After shutdown, I removed the unit's power cord, waited a few seconds, plugged it back in, and restarted the computer. Viola, all the usb ports are functioning properly!

Why the order of battle above, I don't know; but, it worked for me.

---

