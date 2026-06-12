---
title: "Masquerading as a USB key/drive"
date: 2009-07-29
forum: General Help
---

### Post by spip on 2009-07-29
I'm not even sure if the following is possible.

I am looking for something that will allow me to export a certain portion of the filesytem as a fake USB key or drive.  The emulation is not meant for the machine performing though, but rather to another machine connected via USB cable.

The use case I am hoping for is:

1. indicate root folder where fake USB key/drive starts at
2. plug USB cable (will need a USB cable with both ends identical) from computer that is masquerading as the USB key/drive as well as into another computer (computer #2).
3. Computer #2 detects a USB key/drive, when in fact that is being emulated by the first computer.

It is hard to search for something like that as googling for "USB key emulation" or similar subjects will find what you would expect, that is performing local emulation, which is not what I'm looking for.

Any help is much appreciated.

Thanks,
spip

---

### Post by Hobgoblin on 2009-07-29
Your problem is one of terminology.

A computer is a USB host, a USB drive is a USB device, you want the USB host to act as a USB device.

[This may help](http://en.wikipedia.org/wiki/USB) with the terminology but I am not sure what you want exists.  I have seen USB file sharing systems, though these were Windows based and as far as I am aware emulated a network.

Wouldn't an NFS or Samba share do what you want over the network though?

---

