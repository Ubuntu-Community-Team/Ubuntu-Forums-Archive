---
title: "Disk Check Utility"
date: 2010-12-06
forum: General Help
---

### Post by Cokaric on 2010-12-06
Is there any utility that can check and repair my HDD from linux. I have few bad sectors on HDD and because of them I can't Virtualize my Operating System using software Paragon Go Virtual.

I am able to generate virtual copy of each HDD partition separately but I can't virtualize the whole system (whole HDD).

I have 3 NTFS partitions (2 Windows XP partitions and one data partition), one ext3 partition and one swap partition.

I need to BackUp my Current operating system and null the whole drive... I can't perform nulling w/o working Virtual OSs cause I have allot of HWID locked applications on them...

I need someone to help me do this or someone to tell me if he knows a good checking utility for Ubuntu that can check and repair all partitions or if someone knowns other virtualization software that can virtualize my whole computer...

**[EDIT]**
I have already tried repairing my HDD form Windows ( chkdsk /r C:, chkdsk /r E: and chkdsk /r F: ) not once but couple of times. I still get the same error during virtualization.
**[/EDIT]**

Any help is appreciated...

Best regards,
Cokaric

---

### Post by happymellon on 2010-12-06
> **Cokaric said:**
> Is there any utility that can check and repair my HDD from linux.

This can be done by going to:

System > Administration > Disk Utility

Pick your hard disk, and on the right side there is an option for "SMART DATA". Inside there you are able to run three different levels of disk check.

I hope that helps, although if Windows has already performed a low level scan and not fixed it then it sounds like this Paragon software might have other issues. If it doesn't fix it for whatever reason, try checking out Virtualbox, or even VMWare give their player away for free. Virtualbox is in the Software Center, but it looks like VMWare isn't although their viewer is (which isn't the same thing) so you'll have to go to their website to get it.

If you go the VMWare route, take a look at the VMWare disk converter, which is a free product.
[http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)

If you go the Virtualbox route then check out this guide:
[http://www.virtualbox.org/wiki/Migrate_Windows](http://www.virtualbox.org/wiki/Migrate_Windows)

---

### Post by jervin2 on 2011-09-08
So, how do you cause a disk check on a Ubuntu server that doesn't have a desktop gui.

---

