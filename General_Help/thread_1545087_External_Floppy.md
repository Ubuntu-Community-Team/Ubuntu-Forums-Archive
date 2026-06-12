---
title: "External Floppy"
date: 2010-08-03
forum: General Help
---

### Post by Eric-A on 2010-08-03
How can I get ubuntu 10 to recognize and mount an external floppy? "lsusb" can see it, but it sends back error "not properly defined" when I try to format a floppy, and in terminal it gives that error "not in fstab nor mtab. I have even tried a program called *mountmanager* but even that didn't help. The reason I'm doing this is because my mother wants me to add like family pictures to her PC but she only has a floppy drive for file transfers. I stumbled across something, using the command "mount /dev/sdb" from root and it mounts. but it is not plug-n-play, I have to mount and unmount maually using "mount -t vfat /dev/sdb /media/floppy" and "umount /dev/sdb". This is getting frustrating. Any Ideas? I've even added the line /dev/sdb        /media/floppy  auto         rw,user,noauto     0       0 to my fstab to no avail, it will not auto mount when plugged into the usb slot. I have even tried the programs autofs and pmount to no avail.

---

### Post by Eric-A on 2011-01-22
Found the answer right here with usbmount. [http://ubuntuforums.org/showthread.php?t=1470705&page=4](http://ubuntuforums.org/showthread.php?t=1470705&page=4)

---

### Post by djeikyb on 2011-01-22
I'd like to have a moment of laughter at the usage of floppy disks in 2011.

Sorry for the schadenfreude. (Glad you got it worked out)

---

### Post by leonbravo on 2011-09-05
Somehow some of the most current updates of BIOS and firmware in Dell computers still use the floppy drive.

I actually probe one of the options that asseverates keeping the BIOS up to date through repos and didn't work.  

I tried the usbmount and didn't mount the external drive in Dell PowerEdge 2900, 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux.


Any ideas?

---

