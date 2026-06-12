---
title: "GRUB Question"
date: 2011-02-02
forum: General Help
---

### Post by thisnamestoolong on 2011-02-02
Okay -- so I am running a dual boot Windows 7/Maverick setup on my Dell Laptop. I am trying to setup whole disk encryption for the Windows 7 partition (I can't use it for work without whole disk encryption) using TrueCrypt. TrueCrypt is telling me that to run the whole disk encryption for Windows 7, I need to move Grub from the MBR to a partition.

1) Will I still be able to boot Ubuntu, or will the TrueCrypt bootloader frak everything up?
2) Is there a FOSS whole disc encryption solution that supports dual booting?
3) If this is the best solution, how do I do it?

Thanks in advance -- you guys are the best :guitar:

---

### Post by bodhi.zazen on 2011-02-02
> **thisnamestoolong said:**
> Okay -- so I am running a dual boot Windows 7/Maverick setup on my Dell Laptop. I am trying to setup whole disk encryption for the Windows 7 partition (I can't use it for work without whole disk encryption) using TrueCrypt. TrueCrypt is telling me that to run the whole disk encryption for Windows 7, I need to move Grub from the MBR to a partition.

1) Will I still be able to boot Ubuntu, or will the TrueCrypt bootloader frak everything up?
2) Is there a FOSS whole disc encryption solution that supports dual booting?
3) If this is the best solution, how do I do it?

Thanks in advance -- you guys are the best :guitar:

Do you have a wubi installation of Ubuntu ?

Open source encryption would be LUKS, although there are many additional options.

As far as I know, you can not use Truecrypt to encrypt all of your root partition with Linux.

Probably your best option would be to configure the windows boot loader to boot Linux.

---

