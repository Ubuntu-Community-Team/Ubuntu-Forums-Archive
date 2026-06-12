---
title: "USB in Virtualbox?"
date: 2009-12-25
forum: General Help
---

### Post by Unanimated on 2009-12-25
For some reason, my USB doesn't work in Virtualbox. I got the version from the website, not the open source version, I have my user name in the 'vboxusers' group, and I have USB with the USB 2.0 controller enabled in the settings. I have filters on for all four of my USB devices (Logitech mouse, Samsung P3, generic Bluetooth adapter, flash drive) and none of them show up in the guest OS, Windows XP. I also have Guest Additions installed in XP. All of the USB devices are mounted and working in Ubuntu. Clicking 'Devices' on the top bar and then going to USB gives me a list of the devices, but they're all grayed out and I can't click any of them. What's wrong?

---

### Post by gdonwallace on 2009-12-25
You need to install the VBoxGuestAdditions.iso.  This file will enable the USB for the guest OS as well as a couple other options.

VBoxGuestadditions.iso is located in /usr/share/virtualbox.  The easy way to do this is to create a virtual CD attached to the guest OS, and make it load the iso on boot.  This way, you can install the iso from within the guest.  Once installed, remove the virtual CD and you are good to go.

---

