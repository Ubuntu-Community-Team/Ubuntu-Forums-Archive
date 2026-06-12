---
title: "Startup Disk Creator"
date: 2011-10-21
forum: General Help
---

### Post by daz4126 on 2011-10-21
I'm trying to upgrade my Eee Pc to Xubuntu 11.10 using a pendrive. I have used the Startup Disk Creator to create the bootable drive, but it is not being recognised by the computer. It just boots in to the current OS (Xubuntu 11.04).

This worked last time when I installed Xubuntu 11.04 originally. Does anybody have any idea how I can get this to work?

cheers,

DAZ

---

### Post by Artemis3 on 2011-10-22
Try dding the .iso image directly to the usb, that is supposed to work now. Else, try with unetbootin.

Something like: dd bs=100M if=image.iso of=/dev/sdd <- check carefully dmesg for the correct device, after plugging.

---

### Post by plasmafusion on 2011-10-22
the last couple of times i've tried ubuntu's start up disk creator i've had problems. [unetbootin]("http://unetbootin.sourceforge.net/") has never failed me.
the technique described by Artemis3 should work fine though.

---

### Post by daz4126 on 2011-10-23
Thanks for the replies. I've downloaded unetbootin, but it says my usb drive needs to be formatted as FAT32, any idea how I can do this?

thanks,

DAZ

---

### Post by daz4126 on 2011-11-13
I've now tried doing this using unebootin and dd and the result is the same - my netbook just boots into Xubuntu, even though the bios is configured to run the removeable disk first and the iso image is on the pen drive.

Does anybody know what may be the problem and how to fix it?

Thanks,

DAZ

---

### Post by daz4126 on 2011-11-13
Fixed! The problem was with some bizarre bios setting that needed changing.

Sorry to bother anybody and thanks for all the helpful replies.

DAZ

---

