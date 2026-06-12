---
title: "ubuntu lost after partition format!!!"
date: 2011-10-15
forum: General Help
---

### Post by ashhab2010 on 2011-10-15
i bymistake formatted a drive labelled as boot (using gparted) (ubuntu wasnt installed on it) and i even removed the boot flag.when i rebooted my pc both ubuntu and win7 were gone. as i had win7 cd and didnt care for the stuff installed on it i reinstalled win7 but i want ubuntu back as it was before.
plzz help.

---

### Post by TeoBigusGeekus on 2011-10-15
It was probably the partition on which grub was installed.
See [this]("https://help.ubuntu.com/community/Grub2#ChRoot") guide for info on how to reinstall it.

---

### Post by kopiwe on 2011-10-15
Was it a linux boot partition? In this case you should backup your data and reinstall ubuntu.
Also, don't remove boot flags on your partition, they indicate the bios whitch partition is bootable.


If not, you could try to reinstall grub (the bootmanager) again.

Start the live-cd and install grub from there. ( the /dev/sda part is your harddrive, if you have more than one, it could be sdb, sdc, ... etc. Pick the one where ubuntu is installed)
```

sudo grub-install /dev/sda
```Good luck.

---

### Post by ashhab2010 on 2011-10-18
couldnt get live cd or usb to work so now im using the backup method...
which folder should i backup?

edit-
k i booted into ubuntu somehow & tried 

sudo grub-install /dev/sda7 (sda7 is the partition on which ubntu is installd)

but i got an error so i used Boot Repair from TeoBigusGeekus' link and it started working fine but i think the /boot is installd on another partition... will that be a problem?
also the partitition on which boot is installd is not detected by win7... bfore when i had xp it was well detected..why?

---

### Post by ashhab2010 on 2011-10-20
any help?

---

