---
title: "HDD failed is there anyway to mount it to recover data"
date: 2010-02-28
forum: General Help
---

### Post by Fenris_rising on 2010-02-28
Hi All

It seems my 320gb HDD has bitten the dust. The timing couldn't be more ironic as I have spent a couple of days tidying the files on it to burn them to disk.

This is an ntfs drive that had indicated 4 bad sectors but up until today (backup day) was fine. I am unable to mount it and in fact it is causing some sort of conflict with the OS drive and wont let the system boot up successfully.

I am going to try using a windows based PC tomorrow to see if I can rescue the data.

Are there any 'other' tricks to try and mount it with ubuntu that I may not have tried so far? I have tried-

mkdir /media/disk
fdisk -l to establish it's name which was /dev/sdb1 when it was all working but it isn't reachable and doesn't show in the places menu or in any of the menus when using a live CD to get round the HDD clash.
sudo mount -a used in desperation after the mkdir but nothing.

I rejigged the cabling inside the PC to make the HDD a secondary master as it was a slave on the primary IDE to start with in the hope that the system would boot up normally but to no avail.

Any ideas/guides would be gratefully received as there are a few important things I'd really like to rescue.

regards

Fenris

---

### Post by Fenris_rising on 2010-03-01
Never mind. On closer inspection this morning, after a good nights sleep, it seems the failure is hardware rather than disk contents. The platters aren't spinning  =(

regards

Fenris

---

