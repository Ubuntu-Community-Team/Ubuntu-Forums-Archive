---
title: "persistant storage usb stick corrupted, need files back"
date: 2011-05-20
forum: General Help
---

### Post by shortridge11 on 2011-05-20
The story:
I had a usb stick running ubuntu. A coworker used this install to go around some of my companies security measures, and I was told to hold on to the usb stick in question.  I copied all the files onto another usb stick in case something went wrong with the first one.

The problem:
The first usb stick that was bootable has become corrupted. I still have the files from the disc, but they're not on the bootable stick.

Can i just use something like unetbootin, reinstall ubuntu, then drag all the files over?

---

### Post by dabl on 2011-05-20
> **shortridge11 said:**
> 

  I copied all the files onto another usb stick in case something went wrong with the first one.



Do you mean you copied the Linux system files, or that you copied some data files that you had saved there?

If it was the system files, there's no use trying to rebuild a new system from the files of a prior system (a clonezilla disk image would have worked, though).  Just install a new system on the USB stick again, and install Grub on the MBR of the stick, and it will work the same as it did before.  Then if it was data files that you had copied to the other location, just copy them back to the user's home directory on the new system.

---

### Post by shortridge11 on 2011-05-20
i copied every file from the old stick to the new one.  It was just a (ctrl+a) (ctrl+c) (ctrl+v)

---

