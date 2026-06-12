---
title: "Install w/out grub"
date: 2009-12-18
forum: General Help
---

### Post by Canha on 2009-12-18
How do I install Ubuntu Desktop 9.10 without Grub? I want to keep the Windows 7 loader :)

---

### Post by northern lights on 2009-12-18
The Windows 7 loader will not be overwritten by GRUB during setup, but rather [chainloaded]("http://en.wikipedia.org/wiki/Chain_loading") if the Windows entry is selcted. The Windows 7 loader is incapable of booting Ubuntu, so you have to put up with GRUB (it might be possible to replace it with LILO, but that'd be a superfluous move).

---

### Post by amsterdamharu on 2009-12-18
Not sure if grub4dos can load your Ubuntu. It works on xp vista but not sure for Windows 7.

I like to boot with grub myself since it has the command line and you can change the menu entries before booting, good trick if your system won't boot for some reason. But grub4dos has the same thing (I think)

[http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial](http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial)
forget about installing grub4dos, just add entries to your "Windows Vista boot manager" (or whatever is used for win 7)
From the page listed above:
"Use bcdedit to configure the startup menu:     bcdedit /create /d "Start GRUB4DOS" /application bootsector
   bcdedit /set {id} device boot
   bcdedit /set {id} path \grldr.mbr
   bcdedit /displayorder {id} /addlast
Then copy grldr.mbr to C:\, grldr and menu.lst to the root directory of any FAT16/FAT32/NTFS/EXT2 partition. 
Note: previous version of grldr.mbr can also be used in boot.ini of Windows NT/2000/XP/2003. But it doesn't work anymore with the latest version. 
"

After you installed Ubuntu you have to restore the mbr because Ubuntu will install grub in the mbr, before doing so make a copy of the Ubuntu /boot/grub.conf or /boot/menu.lst (on the windows partition so you can read it without starting ubuntu) then edit the menu.lst of Grub4dos to let grub4dos start ubuntu for you (using the info from menu.lst or grub.conf you copied from Ubuntu).

---

### Post by Canha on 2009-12-18
Thanks for your help guys.

---

### Post by john newbuntu on 2009-12-18
At the time of installation, you would install grub into your linux partition or a different partition (not into the MBR).  This is I think in the final step where it says are you ready to install and displays the configuration.  At that point you would click on the advanced button and point grub to be installed in a different partition.
Once you do this, you would issue a "dd" command and copy the Ubuntu bootloader to a file
You could then copy this file to the root directory of Windows 7 and use the windows bcdedit command to chainload Ubuntu with Windows 7.
Here's a fantastic illustration by Iceflatline of how this can be done:
[http://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/](http://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/)

Alternatively, you could use a tool called EasyBCD as described in the link below:
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)
Even though it says vista, win 7 instruction would be very similar I'd imagine.

---

### Post by raymondh on 2009-12-18
2 HD's ?

If so, just install Ubuntu in the 2nd HD and in step 7 of the install process, click advanced and install GRUB in the same HD as Ubuntu. Use BIOS  to control/access the OS'.

---

