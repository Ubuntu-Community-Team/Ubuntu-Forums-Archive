---
title: "Question about apt-get and usbstick boot"
date: 2010-10-07
forum: General Help
---

### Post by apix on 2010-10-07
If i create a usb stick with the applications provided by ubuntu and i choose to save files in the stick (with the available option - cant remember the name), will i be able to install packages and have them available the next time i boot ?

Does anyone know if that is possible ?

Thanks :)

---

### Post by sikander3786 on 2010-10-07
Yes. You can install Ubuntu on the USB stick the normal way you'd have installed it on the HDD i.e, plugin the USB drive, boot off another installation media (CD-ROM or USB stick) and select your USB device as the target device. You can manually partition or Use the entire disc, whatever you prefer. Make sure to install Grub to the USB stick by clicking Advanced button at the last page of installer just before the installation begins.

It is better to disconnect the HDDs before installation so that there is no possiblity of messing up data on the HDDs.

A persistent USB install from System > Administration > Startup Disc Creator should also do the trick. I didn't try it actually.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

