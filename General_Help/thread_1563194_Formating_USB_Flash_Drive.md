---
title: "Formating USB Flash Drive"
date: 2010-08-28
forum: General Help
---

### Post by guy@paprika-software.com on 2010-08-28
I have a 8GB Corsair Flash Voyager drive which I used as a Ubuntu bootable drive to load Ubuntu onto an Acer Aspire. Now I am unable to use the drive for storage and I have been unable to re-format the drive. On Vista the drive is reported as being write protected (there is no physical write protection switch) and on Ubuntu any attempt to re-format the drive fails. GParted can only mount the drive as Read Only.

What I want is a FAT32 partition - I'm happy for the drive to be wiped in the process - there is no data on the drive that I need to keep.

Any idea guys?

---

### Post by Nick_Jinn on 2010-08-28
Is it possible that your device has a little switch on it that puts it in 'read only' mode? Some SDHC chips have that.

Sometimes I have better luck using Knoppix live CD to delete partitions, for some odd reason.

---

### Post by C.S.Cameron on 2010-08-28
I have found that the gparted Live CD is a bit more powerful than the version that comes on the Ubuntu Live CD.

---

