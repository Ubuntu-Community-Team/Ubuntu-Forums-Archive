---
title: "Ubuntu Partition and Acer eRecovery"
date: 2010-08-15
forum: General Help
---

### Post by DOS Boot on 2010-08-15
Hi, I have an Acer Aspire One with Ubuntu installed on it's own partition. Would it be possible to remove that partition with Acer's eRecovery Management program/recovery partition? 

The eRecovery Management program has an option called "Completely Restore System to Factory Defaults" and states that using the option will clear all data on the hard drive and reset the system to it's factory default settings. Would this option remove Ubuntu and GRUB?

---

### Post by MooPi on 2010-08-15
Yes you will need to use either an external CD/DVD drive or make a thumb drive loaded with Ubuntu to do this. Boot to the Live CD via your external drive or thumb drive and start gparted. Through gparted you can manipulate partitions and delete and format to your liking. Ubuntu comes with a thumbdrive utility or you can use another app called unetbootin to load Ubuntu to a thumb drive. Always be careful and backup data before such operations.

---

### Post by DOS Boot on 2010-08-17
> **MooPi said:**
> Yes you will need to use either an external CD/DVD drive or make a thumb drive loaded with Ubuntu to do this. Boot to the Live CD via your external drive or thumb drive and start gparted. Through gparted you can manipulate partitions and delete and format to your liking. Ubuntu comes with a thumbdrive utility or you can use another app called unetbootin to load Ubuntu to a thumb drive. Always be careful and backup data before such operations.

Thanks for the reply. 

Do you think it would be possible to use the hidden recovery partition on the hard drive to remove the Ubuntu partition by restoring the system back to it's factory default settings?

---

### Post by Quackers on 2010-08-17
Yes, it would do that, but it would also re-install Windows back to how it was the day you bought the pc. All updates since that date would then need to be run again. That can take some time. (Unless you can run a backup after the re-installation).

---

### Post by DOS Boot on 2010-08-17
> **Quackers said:**
> Yes, it would do that, but it would also re-install Windows back to how it was the day you bought the pc. All updates since that date would then need to be run again. That can take some time. (Unless you can run a backup after the re-installation).

Thank you for the reply, Quackers. 

Do you know if the recovery image would also overwrite GRUB and replace the Master Boot Record?

---

### Post by RJ12 on 2010-08-17
> **DOS Boot said:**
> Thank you for the reply, Quackers. 

Do you know if the recovery image would also overwrite GRUB and replace the Master Boot Record?

Most likely 99.9% chance that it will. All the recovery really does is usually restore an image of the whole hard drive, that image includes the MBR and will most likely restore the old MBR that came with it (the Windows one) and will kill GRUB. The Ubuntu Live CD / USB will allow you to restore the MBR, but the image will probably kill Ubuntu also.

Edit: It seems that is what you want to do, so I would guess that it will restore the MBR, but I don't have an Acer to test this with.

---

### Post by DOS Boot on 2010-08-17
> **RJ12 said:**
> Most likely 99.9% chance that it will. All the recovery really does is usually restore an image of the whole hard drive, that image includes the MBR and will most likely restore the old MBR that came with it (the Windows one) and will kill GRUB. The Ubuntu Live CD / USB will allow you to restore the MBR, but the image will probably kill Ubuntu also.

Edit: It seems that is what you want to do, so I would guess that it will restore the MBR, but I don't have an Acer to test this with.

Thanks RJ12. Yeah, I basically just want to remove the Ubuntu partition and use a Wubi or Live CD/USB install of Ubuntu, and I figured that maybe the recovery partition was capable of clearing things up.

---

