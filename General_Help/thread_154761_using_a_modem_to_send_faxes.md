---
title: "using a modem to send faxes"
date: 2006-04-03
forum: General Help
---

### Post by sjoseph on 2006-04-03
I am a noob to Linux, like it so far and have transferred much of my work from XP to Ubuntu. I am curious how to set up my modem to send faxes. It seems that I have the software to create a fax, but can't send it. What must I do to enable my modem.

---

### Post by hajk on 2006-04-04
What kind of modem are you talking about? If it is a so-called Winmodem, as in most laptops, then you'll first need a Linux driver for it. Modem must be capable of Fax function, look at the documentation that came with it. Then you'll need a fax programme -- it's a while since I used a combination of mgetty+efax, read the documentation that comes with those packages.

Good hunting!

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

No, I get an error about "FATAL: module not found" for this step

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

### Post by hajk on 2006-04-04
So, you're sure that you have a LinModem, right?

In that case, I'm not sure (judging from your post) what you're trying to do.
It seems to me that it can all be done in a simpler way. Let me give you a part of
my own installation report:

"The Lucent WinModem requires a special Debian driver package, available from [http://linmodems.technion.ac.il/packages/ltmodem](http://linmodems.technion.ac.il/packages/ltmodem) for the installed kernel. If such a package is not available, then the driver source code must first be downloaded, compiled, and packaged. Luckily, there is a compiled package for the latest Breezy 686-kernel.

"The package can then be installed with "sudo dpkg -i <package>.deb", where the package name is substituted, which provides the modules ltserial and ltmodem. These modules are loaded automatically upon boot.

"The ppp0 device can be configured in the Gnome network manager in the usual manner, ..... with use of providers nameservers and setting ppp0 as default gateway. The connection is made once the ppp0 interface is activated.
---

Note that the modules are called ltserial and ltmodem, without underscores!
You may also load them manually with  "sudo modprobe ltserial" (ltserial will pull in ltmodem). The device /dev/ttyLTM0 should now be present, you can check for that.

Good luck!

---

### Post by sjoseph on 2006-04-05
sorry, what i'm trying to do is set up my modem to send faxes, not connect to the internet. i have dsl for the internet.

---

### Post by hajk on 2006-04-05
OK, still need the driver though, you'll know it has been installed right once the device /dev/ttyLTM0 is present. Then you should get mgetty+efax going.

Just follow my instructions given earlier to install the driver (and don't use outdated information, like you were doing).

Cheers!

---

