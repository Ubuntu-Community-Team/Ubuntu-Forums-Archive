---
title: "Wierd install bug?"
date: 2010-06-19
forum: General Help
---

### Post by megamandos on 2010-06-19
ok so, i have multiple drives, and want GRUB2 to be on one, and the OSes on the other, dont ask why. When i go through the ubuntu install, and i get to step 7/7 or w/e, right befor you actually click "install" and I click on "advanced" and then select "install bootloader on another device", or something... I type in "/dev/sde" as my device, then everything goes well until about 95% install and it says:

"Executing 'grub-install /dev/sda' failed.

This is a fatal error."

this is odd, because i have tried this three times, ensuring that I am selecting "/dev/sde" and NOT "/dev/sda", since sda is part of a RAID, and shouldn't me messed with anyways.

Anyone know if this is a bug? I tried doing a manual install of grub, but since I am in the LiveCD right now, it isnt working... i try...


"grub-install /dev/sde"

and i get:
```
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
```

NOTE: /dev is accessible. 

Thanks in advance.

---

