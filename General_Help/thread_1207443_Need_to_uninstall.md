---
title: "Need to uninstall"
date: 2009-07-08
forum: General Help
---

### Post by mrabm on 2009-07-08
Greetings,

I have successfully installed ubuntu  9.04 on my computer on a partition next to Vista but I am running out of disk space for both operating systems.

I will install ubuntu on another computer but I need to uninstall it and clear the partition from this computer.

How do I go about it?

Michel

---

### Post by hansdown on 2009-07-08
Hi mrabm.

Is this a notebook? 

These should help.

[http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html](http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html)

[http://forums.techguy.org/unix-linux/785265-solved-how-can-i-uninstall.html](http://forums.techguy.org/unix-linux/785265-solved-how-can-i-uninstall.html)

[http://echochamber.me/viewtopic.php?f=20&t=38100](http://echochamber.me/viewtopic.php?f=20&t=38100)

---

### Post by ugm6hr on 2009-07-08
[http://members.iinet.net.au/~herman546/p18.html](http://members.iinet.net.au/~herman546/p18.html)

---

### Post by mrabm on 2009-07-08
Thanks for the info and the links. I managed to fix the booting sequence but I still have ubuntu as an option and the space is still low on my hard drive.

How can I now remove ubuntu and clear the partition it has created on my drive?

Thanks,

Michel

---

### Post by AndyCee on 2009-07-08
While we're here...

...Any idea on how to install an NTLDR that supports Vista without the Windows DVD? My wife's laptop has an "install partition", which will simply install an OEM'd Vista without providing the "Windows recovery console".

EDIT: Found "MBR Fix" through ugm6hr's link. Ta.

---

### Post by AndyCee on 2009-07-08
> **mrabm said:**
> Thanks for the info and the links. I managed to fix the booting sequence but I still have ubuntu as an option and the space is still low on my hard drive.

How can I now remove ubuntu and clear the partition it has created on my drive?

Thanks,

Michel
Boot an Ubuntu liveCD, go to System->Administration->Partition editor and do the following:

Delete the ext3 partition & swap
Resize the ntfs or fat32 partition

You might need to right click and "unlock" these partitions. You can't work on any partitions that are mounted.

EDIT: This will not automatically remove an Ubuntu entry in the bootloader menu. You might have to manually re-install whatever bootloader you have (GRUB, NTLDR, LILO etc) to update the entries.

---

### Post by mrabm on 2009-07-08
I downloaded Easeus partition software and simply deleted the ubuntu partition.

Thanks for the info.

Michel

---

