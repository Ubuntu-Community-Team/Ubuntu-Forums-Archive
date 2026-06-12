---
title: "grub loader, disks not recognized by BIOS"
date: 2009-08-10
forum: General Help
---

### Post by CTBuckweed on 2009-08-10
I document this for others that have SCSI drives that are NOT recognized by BIOS. It may also be the case for any drives that are not recognized by BIOS. This issue (I guess) is that BIOS doesn't see the drives but Ubuntu does. Hence, the /boot/grub/menu.lst points to the wrong drives.

My system has an 300GB IDE PATA drive and 2 SCSI drives chained to an Apaptec AHA-29160N controller. I disabled the SCSI BIOS so the SCSI drives are not seen as bootable (or at all in BIOS).

I have a 1GB DOS boot partition on the IDE drive with Windows boot-up software to boot Windows from my SCSI drives. GRUB is also installed on it so I can boot into Ubuntu or Windows.

After (re)installing Hardy onto an IDE partition, it sets the menu.lst wrong and I have to edit it by hand. Everything points to HD2, not HD0. The partition info is correct ( i.e. (HD2,n) in menu.lst )

SYMTPOM: grub fails to boot anything.

Here's excerpts from my menu.lst. I changed the 'root' from (HD2,x) to HD0,x) on all of the boot choices and commented out the 'map' descriptions for my Windows loader.

==============================================
title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=a386a5d7-5523-4217-ad0a-6c39136504bc ro quiet splash
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=a386a5d7-5523-4217-ad0a-6c39136504bc ro single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a386a5d7-5523-4217-ad0a-6c39136504bc ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a386a5d7-5523-4217-ad0a-6c39136504bc ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sde1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
#map		(hd0) (hd2)
#map		(hd2) (hd0)
chainloader	+1
==============================================

I hope this post helps with Ubuntu installations where the BIOS does not recognize the disks.

---

### Post by gosulove on 2009-08-10
i have the grub error 21 problem, and im a complete beginner and whatever ive searched up hasnt worked >.<

any suggestions?

im trying to run jaunty off an external hard drive..but i want to be able to run the default vista without the use of the hard drive, apparently from what ive read my grub was installed to the external hard drive when ubuntu was : /

any fixes? 
thankss

---

### Post by CTBuckweed on 2009-08-23
GoSuLove, I'm not sure what error 21 is. I think I've seen it. Is it when the grub early stages can't find 'menu.lst'?

---

### Post by AmerNewbieInDE on 2009-08-23
> **gosulove said:**
> i have the grub error 21 problem, and im a complete beginner and whatever ive searched up hasnt worked >.<

any suggestions?

im trying to run jaunty off an external hard drive..but i want to be able to run the default vista without the use of the hard drive, apparently from what ive read my grub was installed to the external hard drive when ubuntu was : /

any fixes? 
thankss

unless you chose in install to put grub on the external (step 7, advanced button), it was put on the first drive pointing to the external.

btw.. **21** : **"Unknown boot failure"** This error is returned if the boot attempt did not succeed for reasons which are unknown.

so your pc wont boot?? even to windows? if you dont want grub on your main drive with windows, boot with your windows install disk, goto recovery mode, select dos promt and type fixmbr.. it will rplace the windows boot and get rid of grub. now to put grub on your external, i am not sure, but sure someone here can tell you how to do that

---

