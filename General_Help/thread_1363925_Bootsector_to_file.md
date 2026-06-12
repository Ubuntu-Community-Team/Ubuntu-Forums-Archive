---
title: "Bootsector to file"
date: 2009-12-25
forum: General Help
---

### Post by hakermania on 2009-12-25
Hi all, I was running xp pro sp3 and ubuntu 9.10 on dual boot in my laptop.
Xp crashed and after many tries I wasn't able to boot to xp. Now, I used the dd command to take my bootsector to a folder (dd if= etc) and i put him into my ubuntu 9.10 and into a usb stick as well
Now, I booted into the live cd of ubuntu and I want to restore the boot sector. I want to do the way back. From file to boot-sector. I want to do this because I want to delete the xp's partition and resize my ubuntu one in order to have to the entire hard disk ubuntu.
The problem is that putting the xp's restore CD, not only unable me to boot to ubuntu but also didn't do anything to help booting again to xp!
So, I thought that resizing the ubuntu partition and deleting the xp one from the live CD, would unable me to  boot again to UBUNTU 9.10. So, I thought to run the gparted form my ubuntu 9.10.How? I will boot to my live CD and then i'll mount the ubuntu 9.10 partition, i'll find the gparted command and then i'll run it. In that way it would be like running the gparted from ubuntu 9.10 and not from the cd. But I want to restore the boot sector from /home/alex from the ubuntu 9.10! What is the command from file to bootsector. I googled several times with no many results :(:confused:

---

### Post by dcstar on 2009-12-25
> **hakermania said:**
> Hi all, I was running xp pro sp3 and ubuntu 9.10 on dual boot in my laptop.
Xp crashed and after many tries I wasn't able to boot to xp. Now, I used the dd command to take my bootsector to a folder (dd if= etc) and i put him into my ubuntu 9.10 and into a usb stick as well
Now, I booted into the live cd of ubuntu and I want to restore the boot sector. I want to do the way back. From file to boot-sector. I want to do this because I want to delete the xp's partition and resize my ubuntu one in order to have to the entire hard disk ubuntu.
The problem is that putting the xp's restore CD, not only unable me to boot to ubuntu but also didn't do anything to help booting again to xp!
So, I thought that resizing the ubuntu partition and deleting the xp one from the live CD, would unable me to  boot again to UBUNTU 9.10. So, I thought to run the gparted form my ubuntu 9.10.How? I will boot to my live CD and then i'll mount the ubuntu 9.10 partition, i'll find the gparted command and then i'll run it. In that way it would be like running the gparted from ubuntu 9.10 and not from the cd. But I want to restore the boot sector from /home/alex from the ubuntu 9.10! What is the command from file to bootsector. I googled several times with no many results :(:confused:

This script saves the mbr, modify it to suit your needs to write it to you particular hardware:

```
#!/bin/sh

dd if=/dev/hda of=/mbr-backup bs=446 count=1
```

---

