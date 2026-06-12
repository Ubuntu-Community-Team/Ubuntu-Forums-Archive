---
title: "Cannot mount NTFS partition in Ubuntu Intrepid"
date: 2009-07-30
forum: General Help
---

### Post by davidds on 2009-07-30
:popcorn::KS

root@portatil-david:~# mount /media/Documentos
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda1': Error de entrada/salida
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

Any ideas? :confused:

---

### Post by az on 2009-07-30
Consider hardware problems.

Does it mount in another OS?  If you are still having trouble, consider imaging the partition.  It may be that you have hard drive problems and trying to repair the fileystsme on a damaged disk will lead to further data loss.

You can try to repair the filesystem on the image or simply file-carve most of your data back from the image.

---

### Post by vanadium on 2009-07-30
Do not go for the most difficult scenarios first. Just follow the instructions "In the first case run chkdsk /f ....". 99.99% chance that that will fix your issue.

Linux will not automatically mount unclean ntfs volumes to prevent further corruption. The only way to thoroughly repair an ntfs file system happens to be the Windows. do not forget: ntfs is a proprietary format.

---

