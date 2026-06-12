---
title: "USB Install"
date: 2010-11-09
forum: General Help
---

### Post by eipapp on 2010-11-09
I've been running Ubuntu on a thumb drive to kick the tires, so to speak, and now want to install it on the USB thumb drive and just want to make sure I'm doing this correctly so as not to screw up my internal HD. I've gotten to the point where u allocate drive space and have selected "specify partitions manually". At this point it shows my internal HD with various sda points (ntfs)but under boot loader where it asks for device for boot loader installation I've selected my usb stick /dev/sdc. Can I safely assume that if I take this option that it will indeed install Ununtu on the thumb drive and therefore allow me to run it from the USB stick in the future without affecting my windows OS ?

Thanks & Regards,
Bruce

---

### Post by ki4jgt on 2010-11-09
You need to make sure to install Ubuntu itself in the USB drive by choosing it as the drive you want to install it on. You can actually install the bootloader on a flashdrive and install Ubuntu one the harddrive. Several people use this as a means of security. In that, No USB, no PC! So make sure to have the OS itself and not just the bootloader on the USB.

---

### Post by psusi on 2010-11-09
You can not install to the same usb stick you are booting from.

---

### Post by ki4jgt on 2010-11-09
Also, you may have to format the drive. Most USB drive can not handle the rewritting process and after time wear down. I think Ubuntu has defaultly removed the sdb drives from the list because of this. It is possible to do this, but the drive will not last as well as a normal hard drive.

---

### Post by psusi on 2010-11-09
> **ki4jgt said:**
> Also, you may have to format the drive. Most USB drive can not handle the rewritting process and after time wear down. I think Ubuntu has defaultly removed the sdb drives from the list because of this. It is possible to do this, but the drive will not last as well as a normal hard drive.

No, the drive is not in the list because he is booting from it.  Reformatting will not fix a worn out flash drive.  When it wears out you will just start getting IO errors and the only thing to do is throw it in the trash.

---

### Post by ki4jgt on 2010-11-09
Sorry psusi
You had entered yours before I had finished typing :-)

---

