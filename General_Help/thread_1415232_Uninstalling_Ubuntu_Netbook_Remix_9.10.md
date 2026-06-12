---
title: "Uninstalling Ubuntu Netbook Remix 9.10"
date: 2010-02-24
forum: General Help
---

### Post by DOS Boot on 2010-02-24
Hi, I recently installed Ubuntu Netbook Remix 9.10 in a dual boot configuration with Windows XP on an Acer Aspire One, and Ubuntu's performance seems to be a bit slow overall so I'm in search of the best way to uninstall it. 

Is there a way to safely uninstall Netbook Remix 9.10 and GRUB from the netbook and revert it to a Windows XP-only machine, without losing any data or settings in Windows XP?

Detailed information:

Netbook - Acer Aspire One D250 
Default Operating System - Windows XP 
Linux Operating System - Ubuntu Netbook Remix 9.10
Ubuntu Installation Method - Live USB created using UNetbootin
Goal - Uninstall Ubuntu Netbook Remix 9.10 and GRUB while preserving Windows XP as is.

Any guides, links, or tips on how to properly uninstall Netbook Remix 9.10 would be much appreciated.

---

### Post by drdanielfc on 2010-02-24
> **DOS Boot said:**
> Hi, I recently installed Ubuntu Netbook Remix 9.10 in a dual boot configuration with Windows XP on an Acer Aspire One, and Ubuntu's performance seems to be a bit slow overall so I'm in search of the best way to uninstall it. 

Is there a way to safely uninstall Netbook Remix 9.10 and GRUB from the netbook and revert it to a Windows XP-only machine, without losing any data or settings in Windows XP?

Detailed information:

Netbook - Acer Aspire One D250 
Default Operating System - Windows XP 
Linux Operating System - Ubuntu Netbook Remix 9.10
Ubuntu Installation Method - Live USB created using UNetbootin
Goal - Uninstall Ubuntu Netbook Remix 9.10 and GRUB while preserving Windows XP as is.

Any guides, links, or tips on how to properly uninstall Netbook Remix 9.10 would be much appreciated.

I'm thinking your best bet would be to use gparted to delete your ubuntu & ubuntu swap partititions, then resize the xp one to fill up your entire drive. I'm not sure wether or not your xp bootloader will work again, and if it doesnt you might need to get your hands on an xp disk and use your recovery mode

Note: ive never done this and im not totally sure. id wait for a second opinion if i were you :wink:

---

### Post by DOS Boot on 2010-02-24
> **drdanielfc said:**
> I'm thinking your best bet would be to use gparted to delete your ubuntu & ubuntu swap partititions, then resize the xp one to fill up your entire drive. I'm not sure wether or not your xp bootloader will work again, and if it doesnt you might need to get your hands on an xp disk and use your recovery mode

Note: ive never done this and im not totally sure. id wait for a second opinion if i were you :wink:

Thanks for the reply, unfortunately I do not have access to an external disc drive for the netbook so using recovery discs and such isn't a possibility. 

Also, how does GParted work? Do you use that from inside Ubuntu to delete the Linux partitions and resize the Windows XP one?

---

### Post by DOS Boot on 2010-02-24
Would it be possible to use the hidden recovery partition on the hard drive to wipe out Linux and GRUB? I have used the recovery partition before to reset Windows XP to the factory default settings, but is the recovery partition capable of clearing all partitions on the hard drive or just the default Windows XP partition?

---

### Post by Tourdog on 2010-02-24
Dos Boot,
You use Ubuntu Software Center to download "gparted".   If you have Remix on its own partition and not a wubi install and you delete the 9.10 partition you won't be able to boot XP/ windows.  Grub (where you direct boot 9.10 Remix or XP ) has taken a hit because it belongs to both systems and you deleted part of it.............  You will need to repair the Windows MBR to enable booting up XP again.   The "repair of the MBR" is on this site just do a "search" for it.   Do you do the console cli ?

I have exactly that same Netbook, but used a wubi install of Remix.   Worked very well and that is why now I have Karmic 64 bit on my desktop  (Its own partition).   Wubi is so great to try Ubuntu and if you don't like it or ............   just unplug the USB flash drive or SD flash drive from your Netbook ................  and upon the next bootup ......it is "gone".

HTH!

---

### Post by DOS Boot on 2010-02-24
> **Tourdog said:**
> Dos Boot,
You use Ubuntu Software Center to download "gparted".   If you have Remix on its own partition and not a wubi install and you delete the 9.10 partition you won't be able to boot XP/ windows.  Grub (where you direct boot 9.10 Remix or XP ) has taken a hit because it belongs to both systems and you deleted part of it.............  You will need to repair the Windows MBR to enable booting up XP again.   The "repair of the MBR" is on this site just do a "search" for it.   Do you do the console cli ?

I have exactly that same Netbook, but used a wubi install of Remix.   Worked very well and that is why now I have Karmic 64 bit on my desktop  (Its own partition).   Wubi is so great to try Ubuntu and if you don't like it or ............   just unplug the USB flash drive or SD flash drive from your Netbook ................  and upon the next bootup ......it is "gone".

HTH!

Thanks, I suppose GParted is the way to go then, but will uninstalling Ubuntu with GParted and repairing the MBR allow me to keep my Windows XP install intact?

Also you asked: "Do you do the console cli ?" Are you asking if I know how to use the console/terminal?

---

### Post by Tourdog on 2010-02-24
Dos Boot,
The "cli" was just a heads up.  Search for that "fix" first and as I remember it was a console effort (not a biggee)!   I would use gparted but there are others too.

You won't have a GUI there for awhile so that is the "Console" and the reasons to get all the cli steps you need.

I am pretty sure your XP will remain intact ..............   maybe someone else will hop in here and add some more input.

HTH!

Look at FIXMBR a windows pgm.   Look at SuperGrubDisk............  both of these I found here.

---

### Post by DOS Boot on 2010-02-26
> **DOS Boot said:**
> Would it be possible to use the hidden recovery partition on the hard drive to wipe out Linux and GRUB? I have used the recovery partition before to reset Windows XP to the factory default settings, but is the recovery partition capable of clearing all partitions on the hard drive or just the default Windows XP partition?

Before attempting more in-depth methods to uninstall Ubuntu Netbook Remix, I'd like to know if it would be possible to use the Windows recovery partition to uninstall the Linux partition and GRUB. 

Would using the recovery partition to restore the system to it's factory default settings effectively clear the Linux partition and GRUB from the drive?

---

### Post by DOS Boot on 2010-02-26
Since the default recovery partition seems to be Windows-based will it be capable of clearing the Linux partition and GRUB? Also, would it be capable of repairing the Master Boot Record?

There also appears to be a Linux recovery partition listed in GRUB, would that recovery partition cause any conflicts with the Windows recovery partition?

---

