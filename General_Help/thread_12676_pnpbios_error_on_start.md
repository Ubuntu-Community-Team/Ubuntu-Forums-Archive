---
title: "pnpbios error on start"
date: 2005-01-26
forum: General Help
---

### Post by sherpa on 2005-01-26
Wonder if anyone has seen pnpbios error message during initial boot:

PnPBIOS: Warning! Your PnP BIOS caused a fatal error. Attempting to continue
PnPBIOS: You may need to reboot with the "nobiospnp" option to operate stably
PnPBIOS: Check with your vendor for an updated BIOS
PnPBIOS: get_dev_node: unexpected status 0x28

There is some auto work around which occurs and ubuntu successfully boots.

I've written nobiospnp to /boot/grub/boot.1st ...no effect.

Any suggestions???

Thanks,
sherpa

---

### Post by scoon on 2005-01-26
Hey there, 

Most bios' have a setting in them called PNP or plug and play and can be set to either 'yes' or 'no'.  Go into your bios setup and look for that setting and select 'no'.  The linux knerel does not work well most of the time when that setting is on.  

scoon

---

### Post by sherpa on 2005-01-26
The machine is a sony laptop....does not have a pnp setting in the bios...
Thanks for the speedy reply..
sherpa

---

