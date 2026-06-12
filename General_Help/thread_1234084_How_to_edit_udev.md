---
title: "How to edit udev ?"
date: 2009-08-07
forum: General Help
---

### Post by leegold on 2009-08-07
Hi,

I have a Linksys WUSB54GC USB wifi adapter. The driver is rt73. It's what I think is called a non-kernal driver - I added it myself and works OK as a normal network interface. I'm using Xubuntu 9.04.

I'm trying to get the adapter to work with Kismet. In order to do so I have change something in udev that associated with the adapter and named "USB". I have to change it to something not named "USB", because I'm hearing that that is the cause of an issue I'm experiencing.

I have to: "...to rename your interface by manually editing your udev rules and reloading udev. Name it something that doesn't include 'usb'."

Could anyone tell me how to proceed? I assume the file I should edit is in /dev. Help appreciated.

Lee G.

---

