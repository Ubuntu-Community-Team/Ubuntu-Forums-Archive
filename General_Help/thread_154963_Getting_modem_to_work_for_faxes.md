---
title: "Getting modem to work for faxes"
date: 2006-04-04
forum: General Help
---

### Post by sjoseph on 2006-04-04
I've run scanModem, found the drivers i need, but when i go through the following procedure, i get stuck w the FATAL error at the end, can't find serial _lt module. thoughts....


Modems supported by the Lucent driver

This section is for you if the output of scanModem tells you something like: 'The modem has a supported Lucent/Agere DSP (digital signal processing) chipset.'. You will be able to use a driver from the "restricted-modules" package, which should be installed by default.

    *

      (To check that the necessary package is installed, use your package manager, e.g. Synaptic or Adept. You need to look for a package, which is called linux-restricted-modules-ARCH, where ARCH is the last part of the $ uname -r output, i.e. your kernel flavor. If it is not installed yet, install it there.)

Setup steps:

    *

      In a terminal type

        $ sudo sh -c "echo lt_serial >> /etc/modules"
        $ sudo sh -c "echo lt_modem >> /etc/modules"

      to add them to the module autoloading list.
    *

      Since udev rewrites /dev on each boot, and some dialup programs rely on the existence of /dev/modem, you need to have a symlink created on boot (from /dev/ttyLTM0 to /dev/modem). To do this, create the file /etc/udev/rules.d/10-local.rules, and put these lines in it:

        #ltmodem 
        KERNEL="ttyLTM0", SYMLINK="modem"

    *

      Now load the drivers for the first time:

        $ sudo modprobe lt_serial
        $ sudo modprobe lt_modem

      This should have created the device /dev/modem and you can now go on to configure your dialup connection.
    *

      No, I get an error about "FATAL: module not found" for this step :(

      Note for "5.04 Hoary" users: Ubuntu 5.04 Hoary was shipped with kernel 2.6.10, which has some problems with these modules. To fix, change the grub boot commands /boot/grub/menu.lst as follows (pci=routeirq is new):

        ## ## Start Default Options ##
        ## default kernel options
        ## default kernel options for automagic boot options
        ## If you want special options for specifiv kernels use kopt_x_y_z
        ## where x.y.z is kernel version. Minor versions can be omitted.
        ## e.g. kopt=root=/dev/hda1 ro
        # kopt=root=/dev/hda1 ro pci=routeirq

      Do not forget to update grub: $ sudo update-grub

---

