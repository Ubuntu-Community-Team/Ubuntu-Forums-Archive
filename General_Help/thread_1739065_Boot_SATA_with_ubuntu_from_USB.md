---
title: "Boot SATA with ubuntu from USB"
date: 2011-04-25
forum: General Help
---

### Post by roshanjose on 2011-04-25
Hey,

I have got a situation here....

I have this SATA drive, which I want to connect to my usb drive. Its installed with Ubuntu 10.04. I want to connect it to my laptop using a "SATA to USB connector" and then boot linux. So before I buy this connector/adaptor, can I know if it can be booted from USB? 

Note: My laptop is loaded with Windows7.

---

### Post by wolfen69 on 2011-04-25
Yes it can, just make sure to install GRUB to the external drive.

---

### Post by C.S.Cameron on 2011-04-25
Depends on your BIOS, most modern computers will boot USB.
Select the USB drive as first hard drive in BIOS.

---

### Post by Mark Phelps on 2011-04-26
> **roshanjose said:**
> .. So before I buy this connector/adaptor, can I know if it can be booted from USB?

Only way to KNOW is to try booting from USB.  

If you have a USB stick lying around, you could try using Unetbootin to create a bootable Ubuntu -- and see if you can boot from that.

---

