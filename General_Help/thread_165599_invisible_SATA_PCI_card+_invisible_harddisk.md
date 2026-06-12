---
title: "invisible SATA PCI card+ invisible harddisk"
date: 2006-04-24
forum: General Help
---

### Post by blssurfer on 2006-04-24
Hi, I installed a serial ata iso PCi card from sunix [www.sunix.com.tw](www.sunix.com.tw) lately and upgraded my machine with a serial ata disk, now in windows i installed the driver for the card and the disk was there in the system.
Here in kubuntu i can't find neither the card nor the disk(none is listed as a device), any ideas on how to proceed?

--Have a nice day.

---

### Post by blssurfer on 2006-04-24
Update: in fact i can see the card under pci devices, 0000:00:0F.0 0106 Initio corporation: Unknown Device 1622 (rev02) ... ... ... sounds spanish to me..

---

### Post by blssurfer on 2006-04-24
Aha the sunix obsolete driver says the open source driver is included since version 2.4 of the kernel.. so why is it not working??

---

### Post by blssurfer on 2006-04-24
After some research it seems i should do something like this... hdparm -X69 -d1 /dev/hde but i don't want to kill my machine yet :(
Anyway does anyone have a clue what this means?

---

### Post by blssurfer on 2006-04-25
ok, problem can't be solved... This manufacturer sunix changed the chipset for the card, now it is based on the INITIO 1622TA2 serial ata driver chip. This chip has no driver for linux, it doesn't even show up in the "maybe developed in the future list". 
My advice, don't get anything from SUNIX, they sell supposedly linux compatible products that are not, not even close.

---

