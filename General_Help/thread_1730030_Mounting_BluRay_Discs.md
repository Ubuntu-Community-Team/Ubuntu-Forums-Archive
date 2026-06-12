---
title: "Mounting BluRay Discs"
date: 2011-04-15
forum: General Help
---

### Post by stuart_waring on 2011-04-15
I have manually set my fstab file to mount anything inserted into my primary optical drive (designated sr0) into a specific folder in the \media folder to allow me to use the drives on the newtwork. This works fine with any dvds and CDs, whether they are movie discs or data discs. When i insert a blu ray i get the following message

Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I have checked the dmesg|tail file and this is what it says

[  172.820257] ISO 9660 Extensions: Microsoft Joliet Level 3
[  172.822439] ISOFS: changing to secondary root
[  300.525821] ISO 9660 Extensions: Microsoft Joliet Level 3
[  300.528372] ISOFS: changing to secondary root
[  303.283256] ISOFS: Unable to identify CD-ROM format.
[  343.384509] ISOFS: Unable to identify CD-ROM format.
[  636.908081] ISOFS: Unable to identify CD-ROM format.
[  856.559567] ISOFS: Unable to identify CD-ROM format.
[  895.612049] ISOFS: Unable to identify CD-ROM format.
[  982.840462] ISOFS: Unable to identify CD-ROM format.

When i remove the code from the fstab file, it mounts fine.

Any ideas on how to solve this?

Thanks
Stuart

---

