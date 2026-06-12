---
title: "installing ubuntu on pen drive"
date: 2011-04-19
forum: General Help
---

### Post by ubun2warrior on 2011-04-19
hi

can i install ubuntu straight to my pendrive instead of the hard disk ?? will it work faster from pendrive??

regards

---

### Post by garvinrick4 on 2011-04-19
Yes you can install to a pen drive and it will be slower.

---

### Post by Megaptera on 2011-04-19
Similar question here [http://ubuntuforums.org/showthread.php?t=1732807](http://ubuntuforums.org/showthread.php?t=1732807) with useful links etc.

---

### Post by ubun2warrior on 2011-04-19
> **garvinrick4 said:**
> Yes you can install to a pen drive and it will be slower.

why will it be slow?? i thought that flash memory is fast...

---

### Post by varunendra on 2011-04-20
> **ubun2warrior said:**
> hi

can i install ubuntu straight to my pendrive instead of the hard disk ?? will it work faster from pendrive??

regards
Yes, as garvinrick4 already said.
Just make sure you choose "Advance" option while installing grub, and then choose your pendrive as the destination for grub (eg. sdb or sdc - whatever your pendrive is listed as, NOT sdb**1** or sdc**1** etc.). If you don't do this, the system will always require the pendrive to be plugged in order to boot. Because the grub mbr will by default be written on your fixed hard drive and will look up the pendrive for its boot configuration files.

> **ubun2warrior said:**
> why will it be slow?? i thought that flash memory is fast...
Yes the flash memory is fast, but the USB so far is not. The rated transfer speed of USB 2 is 480 Mbps (=60 MBps), however, excluding the communication overhead, the practical speed falls down to 25-30 MBps (see [here]("http://en.wikipedia.org/wiki/Universal_Serial_Bus#Transfer_speeds_in_practice")).

The practical data transfer speeds for a typical SATA drive is around 45-75 MBps (see [here]("http://www.tomshardware.com/forum/253182-32-sata-transfer-speeds"))

Hope it explains why pendrives are not as fast as HDDs.

---

