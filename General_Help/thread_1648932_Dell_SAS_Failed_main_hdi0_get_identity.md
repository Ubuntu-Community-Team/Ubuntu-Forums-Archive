---
title: "Dell SAS Failed main hdi0_get_identity"
date: 2010-12-19
forum: General Help
---

### Post by ishti10 on 2010-12-19
I get this message at the startup of ubuntu 10.04 on my Dell SC1435 Poweredge Server.
Failed Main hdi0_get_identity /dev/sdb

/dev/sda1 is the first hard disk on the SAS  controller card. It is a Serial Attached SCSI drive.
/dev/sdb1 is the second hard disk on the SAS controller card. It is a Sata Drive.

/dev/sda1 is the bootable drive and /dev/sdb1 is mounted via fstab.

Nothing seems to be wrong, /dev/sdb1 seems to be accessible and I can copy files between drives at 60 MB/s.

But still I would like to make sure and remove the message properly.
So I sincerely ask for some help and guidance from fellow ubuntu users.

---

### Post by piquat on 2010-12-20
Take this with a grain of salt but I think it's complaining about not finding a UUID for that drive.  Why?  I have no idea.  Might give you an item to start searching for though.  Maybe someone else will come in here with more information....

---

### Post by Linux_junkie on 2010-12-20
As the SAS are a secret special forces unit I'm not surprised its not giving you anything as their trained not to give information even under interrogation.

---

