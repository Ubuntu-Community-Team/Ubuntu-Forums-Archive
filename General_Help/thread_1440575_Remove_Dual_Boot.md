---
title: "Remove Dual Boot"
date: 2010-03-27
forum: General Help
---

### Post by bldaun on 2010-03-27
Prior to installing ubuntu I had an installation of Vista Ultimate on my computer. I kept that OS and installed ubuntu on a clean second hard drive. The Vista installation included a small program called Vista Boot Pro which allowed me to dual boot to either vista or the empty hard drive. Since installing ubuntu I now have many options when booting including ubuntu and Vista. Ubuntu added a series of other options that were not present originally. Is there a way to uninstall the dual boot option from ubuntu and just use the vista dual boot program (VistaBootPro)?
 
If I need to clarify further please let me know.
 
Thanks 
 
Bob

---

### Post by Serpher on 2010-03-27
What you can do is type in the following command in a terminal:

```
sudo gedit /boot/grub/grub.cfg
```

Or for versions 9.04 and below:

```
sudo gedit /boot/grub/menu.lst
```

The bottom and upwards of this file is your GRUB (The bootloader Ubuntu uses) menu. You can change the 'title' property to whatever you want, and also remove entries if you're mindful of the '}' brackets. To remove them, you can delete them, or it's best just to put '#' at the beginning of each line you want to delete, making your computer just read those lines as code comments, not being executed.

This will obviously keep your current bootloader GRUB, but allow you to have the menus anywhere you want. You can even copy paste the Windows part of it at the top, so it starts be default automatically. You can also change your timer settings. Keep in mind though it's important to make a backup of this file as if you screw it up, you can't boot...also will be nice to have a Live CD hanging around in case you can't boot. To back up this file use the following command.

```
cp /boot/grub/grub.cfg ~/Desktop/
```

Replace grub.cfg with menu.lst if you have Ubuntu 9.04 and below. Also please make sure you are mindful that brackets are going where they're supposed to go.

---

### Post by mr clark25 on 2010-03-27
i am 95% sure that the vista booter wont work with ubuntu. im almost sure that it only works with versions of windows.

i could be wrong.

---

### Post by Mark Phelps on 2010-03-27
> **bldaun said:**
>  Is there a way to uninstall the dual boot option from ubuntu and just use the vista dual boot program (VistaBootPro)?

Answer really depends on what you're using to boot now.

If you're booting using GRUB, you would need to restore the Vista MBR and then remove GRUB.  If you so the second thing first, you will not be able to boot anymore.

If you're booting using VistaBootPro, all you would have to do is remove the Ubuntu entry.

---

### Post by bldaun on 2010-03-28
Thanks to all for your ideas.  Have not had a chance to investigate yet but I will try a couple of things in the near future.  This is a convenience thing and does not keep me from proceeding with my Vista or Ubuntu investigations.
 
Bob

---

