---
title: "Nvidia driver not loading"
date: 2010-08-10
forum: General Help
---

### Post by pedro1hayling on 2010-08-10
Hi
I have been using Ubuntu since vers 6.04 - with very few problems even in the early days, but since the last upgrade to 10.04LTS am having problems with the Nvidia driver not loading - at boot I'm getting a box coming up in the centre of the screen offering various choices, one of which is to restart the Xserver - having done that and confirmed it - ubuntu will continue to boot and all's well - this is not normal and becoming rather tedious -

 

the system is also reporting no proprietory  video drivers installed - altering the nvida settings from the apps menu has no effect.

None of the known issues for Lucid appear to cover this one

---

### Post by NewDisciple on 2010-08-10
Is the driver enabled/activated in system/admin/hardware drivers?
Which version of driver and what version of card?

---

### Post by ub-newbie on 2012-02-04
Since I'm having the same problem, let me answer.

First, UB 10.04 (Lynx)X64, problem showed up after kernel upgrade.

Card is onboard GeForce 8300
Driver?? 
When I start the "NVIDIA X Server Settings" it says 
"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

I have ran ```
sudo nvidia-xconfig
``` and rebooted, but I still get the same result, a box with choices, and "restart xserver" causes it to work.

"cat /var/log/Xorg.0.log" gives

```

(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(EE) NVIDIA:Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA:system's kernel log for additional error messages.
(II) UnloadModule: "nvidia"
(II) Unloading /usr/lib/xorg/extra-modules/nvidia_drv.so
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

Fatal server error:
no screens found
```


Any suggestions??

---

### Post by Bobhuber on 2012-02-04
Have you tried booting into  the previous Kernel ?

---

### Post by ub-newbie on 2012-02-04
Bob, I had not (but that would have solved it).

Problem was PEBKAC.  

It appears that I had ACCIDENTALLY installed 2.6.32-38 kernal, but not the kernal headers.  In MESSAGES I found 
```
Feb  4 10:46:49 tv dkms_autoinstaller: nvidia-current (195.36.24): Installing module on kernel 2.6.32-38-generic.
Feb  4 10:46:49 tv dkms_autoinstaller:   Kernel headers for 2.6.32-38-generic are not installed.  Cannot install this module.
Feb  4 10:46:49 tv dkms_autoinstaller:   Try installing linux-headers-2.6.32-38-generic or equivalent.
```

Then I installed the headers, but at the same time tried a different (older) NVIDIA driver (causing problems).

The solution, switch back to current NVIDIA driver, reinstall 2.6.32-38 Kernel & Kernel Headers, reboot, bask in my own glory.

---

