---
title: "is it possible to apply a firmware update via WINE"
date: 2011-05-21
forum: General Help
---

### Post by eltonw on 2011-05-21
I am experiencing a problem reading long filenames on dual-layer 8.5 Gb DVDs. 
Please SEE: [http://ubuntuforums.org/showthread.php?p=10846675#post10846675]("http://ubuntuforums.org/showthread.php?p=10846675#post10846675")

_[COLOR="Olive"][FONT="Verdana"]I am considering a possible solution might be a firmware update.[/FONT][/COLOR]_

The drive is a **Toshiba-Samsung : SE-S084B/RSBN** [**TSST**=Toshiba Samsung Storage Technology Corp]
Samsung provides ONLY windows updates or a web-based *windows-only* method of installing same.
SEE: [http://www.samsung.com/sg/support/detail/supportPrdDetail.do?menu=SP01&prd_ia_cd=1601&prd_mdl_cd=SE-S084B%2FRSBN&prd_mdl_name=SE-S084B&srchword=SE-S084]("http://www.samsung.com/sg/support/detail/supportPrdDetail.do?menu=SP01&prd_ia_cd=1601&prd_mdl_cd=SE-S084B%2FRSBN&prd_mdl_name=SE-S084B&srchword=SE-S084")

**Is it possible to apply a firmware update using WINE?**

---

### Post by dabl on 2011-05-21
No.

You can make a bootable MS-DOS floppy, or a Win 98 "Rescue Diskette", or something like that, which will work for firmware updating, but wine does not address your real hardware -- it is a translation layer between the Linux OS and your Windows applications.  The Linux OS is what addresses the hardware layer of your system, while it is running.

---

### Post by eltonw on 2011-05-21
Damn! neither machine has a diskette drive (both are portables). I guess one can never be free of Windows. <*SIGH*>

---

### Post by CTBuckweed on 2011-05-21
> **eltonw said:**
> Damn! neither machine has a diskette drive (both are portables). I guess one can never be free of Windows. <*SIGH*>

They have USB ports right? Buy/borrow/steal someone's USB floppy drive.

---

### Post by dabl on 2011-05-24
Understanding from the OP that there is a problem with the optical drive, you should be able, one way or another, to either boot a MS-DOS Live CD, or to make a MS-DOS bootable USB stick from a CD ISO image.  Here are the images:

[http://www.allbootdisks.com/download/iso.html](http://www.allbootdisks.com/download/iso.html)

If your optical drive won't boot a bootable CD, then you'll have to mount the ISO image, copy the contents onto a prepared (empty) USB stick, then install Grub on the USB stick to make it mountable.  There is guidance on how to do that under "Method #2" here:

[http://kubuntuforums.net/forums/index.php?topic=3107512.0](http://kubuntuforums.net/forums/index.php?topic=3107512.0)

Once you have MS-DOS running on the computer, you can copy your upgrade flash file to it, and execute it, to do the firmware upgrade.

---

