---
title: "Cannot install Ms-sys-2.2.1"
date: 2011-02-17
forum: General Help
---

### Post by Ciro-Vaune on 2011-02-17
Hello All.

I am trying to create a boot-able flash drive of Windows 7.  I have the .iso and the flash drive.
[http://serverfault.com/questions/6714/how-to-make-a-windows-7-usb-flash-install-media-from-linux](http://serverfault.com/questions/6714/how-to-make-a-windows-7-usb-flash-install-media-from-linux)
That article covers the creation process rather well, however i have one problem.  I cannot seem to get
ms-sys installed to create a boot record.

I download the newest stable build from Sourceforge, navigate to the directory, and execute the make command.  After that it says to issue the install command, and it quits with errors.

The make command ends with:
> 
mkdir -p mo
msgfmt -o mo/sv.mo po/sv.po
make: msgfmt: Command not found
make: *** [mo/sv.mo] Error 127
And the install command puts out:
> 
install -D -m 755 bin/ms-sys /usr/local/bin/ms-sys
msgfmt -o mo/sv.mo po/sv.po
make: msgfmt: Command not found
make: *** [mo/sv.mo] Error 12
I'm still quite new to Linux.  What could I be doing wrong?

---

### Post by Yofel on 2011-02-17
You don't have the msgfmt application installed. Try installing the 'gettext' package.

---

### Post by Ciro-Vaune on 2011-02-17
Thank you very much.  I knew it was a simple error.

---

### Post by Ciro-Vaune on 2011-02-17
Nevermind.

---

### Post by WorMzy on 2011-02-17
```
sudo fdisk -l
```

Chances are your USB drive will be the last in the list, but just in case it isn't, you should be looking for other giveaways. e.g. this is my output:

```
Disk /dev/sdd: _4026 MB_, 4026531840 bytes
124 heads, 62 sectors/track, 1022 cylinders, total 7864320 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          62     7857135     3928537    c  _W95 FAT32 (LBA)_

```

The device size (4026MB) and the only partition's filesystem (FAT32) make it pretty clear that it's a USB stick.

---

