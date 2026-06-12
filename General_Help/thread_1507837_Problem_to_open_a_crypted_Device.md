---
title: "Problem to open a crypted Device"
date: 2010-06-12
forum: General Help
---

### Post by amineurin on 2010-06-12
Hello,

i got a serious problem over here. I have a crypted HDD and i never had a problem to open it with the following command:

root@ubuntu:/mnt/root# cryptsetup -c serpent-cbc-essiv:sha256 -s 256 -d passwd luksOpen /dev/disk/by-id/scsi-SATA_Hitachi_HDS7220_JK1180YAHD72MT sdd

But now i changed my Ubuntu version and i am not longer able to open it :(

Im getting the following message:

> No key available with this passphrase.

i checked /var/log/messages and i saw :


> ubuntu kernel: [  431.221031] alg: No test for cbc(serpent) 

Please help ..because there are really important files on that drive!


Really nobody with any idea around? - please!

---

