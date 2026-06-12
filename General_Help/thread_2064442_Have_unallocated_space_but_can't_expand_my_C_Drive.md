---
title: "Have unallocated space but can't expand my C:/ Drive!!!"
date: 2012-09-29
forum: General Help
---

### Post by Eirreann on 2012-09-29
Okay, so here's the issue:
[IMG]http://i296.photobucket.com/albums/mm188/Loredaen/Partitionsandjunk.png[/IMG]

That 28GB of unallocated space is what I had left over after my installation of Ubuntu 12.04 (I used the disk manager on the Live CD to deduct that 28GB from the /home partition)
However, now I cannot expand my C:/ drive to utilise that 28GB of free space!  Can anyone help me out?
If it isn't possible to give that space back to Windows, can someone at least tell me how to re-add it to the /home partition?
Thanks in advance!

---

### Post by kc1di on 2012-09-29
I think your problem is that windows c: partition has to be all together on the drive. but you should be able to designate it as a separate Windows partition just make drive D: or E or whatever.
and format it as NTFS or Fat32.

---

### Post by agillator on 2012-09-29
kc1di is right. To add the 28GB to the Windows partition you would first need to move all the other partitions to the right so the unallocated space immediately followed the Windows partition, then you could resize the Windows partition to include that unallocated space. Then you would probably have to reinstall GRUB since the partitions had all changed or you would be unable to boot. The chances of making an unrecoverable error during all this are very high. Additionally, moving ONE partition can take a matter of hours. Moving that many . . . . If you really want that space usable by Windows, follow the suggestion and simply format it as an NTFS or FAT32 file system for Windows to use as drive D: or something.

---

### Post by Eirreann on 2012-09-29
> **agillator said:**
> kc1di is right. To add the 28GB to the Windows partition you would first need to move all the other partitions to the right so the unallocated space immediately followed the Windows partition, then you could resize the Windows partition to include that unallocated space. Then you would probably have to reinstall GRUB since the partitions had all changed or you would be unable to boot. The chances of making an unrecoverable error during all this are very high. Additionally, moving ONE partition can take a matter of hours. Moving that many . . . . If you really want that space usable by Windows, follow the suggestion and simply format it as an NTFS or FAT32 file system for Windows to use as drive D: or something.

Yikes!  Well I definitely don't want that!  Yeah, I guess I'll be making it into a new, usable volume.  Thank goodness Steam gives you the option to install to specific locations, now, haha!  Thanks for the help, guys!

---

