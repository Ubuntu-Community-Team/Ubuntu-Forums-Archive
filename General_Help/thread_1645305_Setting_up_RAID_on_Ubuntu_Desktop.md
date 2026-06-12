---
title: "Setting up RAID on Ubuntu Desktop"
date: 2010-12-14
forum: General Help
---

### Post by Ceiber Boy on 2010-12-14
I tried installing ubuntu 10.10 in a RAID0 configuration (on two HDD) but the install process dose not seam to allow me to do it! is it possible to set up RAID on ubuntu desktop? if so how?

Thanks

---

### Post by dabl on 2010-12-14
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Be aware that Linux does not support all of the consumer-grade motherboard SATA RAID chips, which are actually not a complete RAID controller, but are referred to as "fakeraid".  They use some software (typically in the included Windows driver) and the Linux kernel does not have 100% of all driver modules needed for all the chip models.

Also google "dmraid" and "mdraid" to learn about full software RAID.

If it's really important for data security (i.e. a commercial installation), get a serious hardware RAID controller, with Linux driver support, such as these:

[http://www.3ware.com/products/serial_ata.asp](http://www.3ware.com/products/serial_ata.asp)

---

### Post by Ceiber Boy on 2010-12-19
Thanks for the reply - the reading was pretty comprehensive. answered all my questions!

---

