---
title: "Preserving Multiboot Setup on Selective Reinstall"
date: 2010-09-14
forum: General Help
---

### Post by Reliable on 2010-09-14
I've set up a multiboot with XP, Vista, Windows 7, and Ubuntu 10.04.1, installed in that order in five individual partitions on a single hard drive (fifth is for the Ubuntu swap area).  Everything is working well: On boot, the GRUB menu comes up first, with the usual Ubuntu choices and "Windows 7 (loader)".  When I select that last option, I'm then given the Windows boot menu that allows "Earlier Version of Windows", "Windows 7", and "Microsoft Windows Vista".  They all boot properly, and I don't mind having to use the second menu.  I would like to reinstall XP (only) to the same partition it now occupies.  I suspect this will mess up my current booting scheme, correct?  Is there a way I can prevent this, by saving the GRUB configuration or whatever?

---

### Post by wilee-nilee on 2010-09-14
> **Reliable said:**
> I've set up a multiboot with XP, Vista, Windows 7, and Ubuntu 10.04.1, installed in that order in five individual partitions on a single hard drive (fifth is for the Ubuntu swap area).  Everything is working well: On boot, the GRUB menu comes up first, with the usual Ubuntu choices and "Windows 7 (loader)".  When I select that last option, I'm then given the Windows boot menu that allows "Earlier Version of Windows", "Windows 7", and "Microsoft Windows Vista".  They all boot properly, and I don't mind having to use the second menu.  I would like to reinstall XP (only) to the same partition it now occupies.  I suspect this will mess up my current booting scheme, correct?  Is there a way I can prevent this, by saving the GRUB configuration or whatever?

I would go to the windows 7 forums and ask for help there as well. The reason being as your whole MS boot is probably attached to that XP partition and if overwritten, you will need some help from somebody that knows this stuff. I am fairly sure you would lose your boot for the other 2 MS setups. There are ways of doing this and I am fairly sure there are people on this forum who can help, but your wait time might be a bit longer.
[http://www.sevenforums.com/](http://www.sevenforums.com/)

---

### Post by oldfred on 2010-09-15
As wilee-nilee says windows has combined its boots into the one with the boot flag (primary partition). You might want to look at boot.ini as it may have the setting but generally win7 will copy all of its boot files into the XP partition so you probably are using a BCD. Reinstalling XP will not see the Vista & 7 as they are newer and you will be missing all the boot files from Vista & 7.

You will have to reinstall grub or grub2 as a windows install automatically overwrites the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by Reliable on 2010-09-15
Thanks to both of you.  I'll proceed, using the links you provided and other info I've found, and let you know how it turned out.  I'll mark this as solved once I post back.

---

