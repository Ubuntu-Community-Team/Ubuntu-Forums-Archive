---
title: "Problems with USB since update"
date: 2012-03-09
forum: General Help
---

### Post by Tymoniden on 2012-03-09
Hi,
i recently did an update (march 9th 2012) and after rebooting the system all USB devices aren't working anymore.

I get the following message in /var/log/syslog when i plug in my mouse or keyboard

[PHP]Mar  9 10:19:37 steib kernel: [ 1129.756345] usb 3-1: new full speed USB device number 10 using xhci_hcd
Mar  9 10:19:37 steib kernel: [ 1129.756441] usb 3-1: Device not responding to set address.
Mar  9 10:19:37 steib kernel: [ 1129.960151] usb 3-1: Device not responding to set address.
Mar  9 10:19:38 steib kernel: [ 1130.163803] usb 3-1: device not accepting address 10, error -71[/PHP]I'm using Ubuntu 11.10 on a Dell Vostro V131

I hope someone can help me.

best regards and thanks,
Timo

---

### Post by pavi_elex on 2012-03-09
Install xorg
    sudo apt-get install xserver-xorg
    sudo apt-get install xserver-xorg-core
if it is already installed
Reconfigure xorg
    sudo dpkg-reconfigure xserver-xorg

if it does not help,
try to "fix broken packages" in Recovery mode.

---

### Post by matt_symes on 2012-03-09
Hi

Do the devices start working if you boot into an older kernel ? Do they work from a LiveCD/USB. Just trying to eliminate hardware.

Kind regards

---

### Post by tmeitner on 2012-03-09
This is not a hardware issue, as the same thing happened to me after updating this morning. My USB wireless connection suddenly gave out, and after rebooting, I lost my USB mouse and keyboard as well.

After running "sudo dpkg-reconfigure xserver-xorg" and waiting a couple minutes, the mouse and keyboard show up again under "lsusb". However, it takes another minute or two before they begin to work, and I still have not figured out how to regain connection through my USB wireless dongle.

In other words, since the update this morning, my Ubuntu desktop is pretty useless. I'm running an eMachines EL1358G desktop.

EDIT/UPDATE: I unplugged and re-plugged in my USB wireless dongle and I am connected to the internet again. Not sure what's going on here.

---

### Post by matt_symes on 2012-03-09
Hi

Are these USB 3 controllers ?

Kind regards

---

### Post by tmeitner on 2012-03-09
> **matt_symes said:**
> Hi

Are these USB 3 controllers ?

Kind regards

Nope - these are all USB 2. They all worked out-of-the-box (and actually, with several Ubuntu versions) before this morning's update.

---

### Post by matt_symes on 2012-03-09
Hi

Are the USB drivers being bound correctly to the kernel ?

[http://lwn.net/Articles/143397/](http://lwn.net/Articles/143397/)

Kind regards

---

### Post by Tymoniden on 2012-03-13
yeah "sudo dpkg-reconfigure xserver-xorg" worked for me as well. Thanks!

---

