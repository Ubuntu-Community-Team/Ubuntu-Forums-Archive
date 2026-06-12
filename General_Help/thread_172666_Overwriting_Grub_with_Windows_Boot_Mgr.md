---
title: "Overwriting Grub with Windows Boot Mgr?"
date: 2006-05-09
forum: General Help
---

### Post by adduds on 2006-05-09
Hey ALL! :)

I have a dual hard drive tower. The master drive containing windows, slave containing ubuntu BB. Now I want to take ubuntu off, but I use the Grub to dual boot the computer. How do I remove ubuntu and re-install the Windows Boot Manager??

cheers all,
ad

---

### Post by Sef on 2006-05-09
> Now I want to take ubuntu off, but I use the Grub to dual boot the computer. How do I remove ubuntu and re-install the Windows Boot Manager??

Windows Boot Manager can't see Linux, only Windows.

---

### Post by Thirsteh on 2006-05-09
Type this:

```
sudo dd if=/dev/zero of=/dev/hda bs=512 count=1
```

It will clear the MBR and data of your harddrive, including the boot manager and all files.

---

### Post by adduds on 2006-05-09
[QUOTE=Thirsteh]Type this:

```
sudo dd if=/dev/zero of=/dev/hda bs=512 count=1
```

It will clear the MBR and data of your harddrive, including the boot manager and all files.[/QUOTE]

Will I be able to boot windows after though?

---

### Post by Thirsteh on 2006-05-09
No, everything on the drive will be erased, or, it won't, but the Windows partition won't be there anymore. If you want to keep your installed Windows you might not be looking for my solution :)

---

### Post by adduds on 2006-05-09
[QUOTE=Thirsteh]No, everything on the drive will be erased, or, it won't, but the Windows partition won't be there anymore. If you want to keep your installed Windows you might not be looking for my solution :)[/QUOTE]

K, ya i'm looking to remove Ubuntu off the slave drive, which unfortunately controls boot w/ Grub. While keeping windows intact on the master drive, which case I would then need to re-install the WBM or WBR

any solutions peoples?

cheers,
ad

---

### Post by Thirsteh on 2006-05-09
oh, it's on another drive.

There should be an option when using the Recovery mode with the Windows CD -- one that will restore the Windows boot loader.

---

### Post by Reshin on 2006-05-09
Boot from windows cd and go to rescue console. From there type "fixmbr" and that's that

I think you should also check that windows-partion has boot-flag on it with gparted or whatever

---

### Post by PvSinNL on 2006-05-09
[QUOTE=Sef]Windows Boot Manager can't see Linux, only Windows.[/QUOTE]
I'd like to add that, although Windows is unaware of Linux partitions, it's possible to boot Linux from the Windows (XP/2k) boot menu using a few simple tricks. See, e.g., [this page]("http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html") for detailed instructions.
(Don't ask me why, but I prefer to have the XP boot manager on the MBR instead of GRUB...)

---

