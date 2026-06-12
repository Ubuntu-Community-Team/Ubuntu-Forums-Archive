---
title: "Installed GRUB4DOS, Now Windows Won't Load"
date: 2010-12-12
forum: General Help
---

### Post by Nathaniel D. on 2010-12-12
Not sure if this is the right forum for this, but I see Linux users knowing more about Windows than Windows users know about Linux. ;-)

So I was trying to create a flash drive from my family desktop computer (Windows Vista) to install GRUB on my laptop (Arch Linux/Windows XP), according to the directions of this video:
[http://www.youtube.com/watch?v=voXiegv9bNA](http://www.youtube.com/watch?v=voXiegv9bNA)

But when I booted up the desktop the next morning, it brought me to the Windows Boot Manager, which gave me the option of starting "Windows Vista (TM) Home Premium (recovered)", "openSUSE 11.2 installer (NET)", or using the tool "Windows Memory Diagnostic"
Starting either Vista or openSUSE gets me:

```

  Booting 'openSUSE 11.2 installer (NET)'

 (hd0,0)
 Filesystem type is ntfs, partition type 0x7
kernel /openSUSE/linux devfs=mount,dall ramdisk_size=65536 install=ftp://ftp4.g
wdg.de/pub/opensuse/distribution/SL-OSS-factory/inst-source/ server=ftp4.gwdg.d
e lang=en splash=silent vga=normal

Error 17: File not found

Press any key to continue...

```Pressing a key brings me to the GRUB4DOS boot menu (which appears to be pretty much the same as a normal GRUB menu). The only boot option there is openSUSE 11.2 installer (NET), the starting of which brings me back to the previous screen.

If I select Windows Memory Diagnostic in Windows Boot Manager, it gives me:
```

Windows failed to start. A recent hardware or software change might be the 
cause. To fix the problem:

  1. Insert your Windows installation disc and restart your computer.
  2. Choose your language settings, and then click "Next."
  3. Click "Repair your computer."

If you do not have this disc, contact your system administrator or computer
manufacturer for assistance.

    File: \boot\memtest.exe

    Status: 0xc0000225

    Info: The selected entry could not be loaded becuse the application is
             missing or corrupt.

```Now I know GRUB installed to the flash drive, because I booted from the flash drive on the laptop (though it turned out I couldn't install GRUB, as it was for a windows operating system). When I was on grubutil, I didn't plug in my flash drive until I had checked the dropdown list of disks, so that when I refreshed it, I knew which one was the flash drive (hd5), and the size of hd5 also matched up (though a tad bit less) with the size of my flash drive.

Additional Information:
The desktop was a floor model, so we don't have any installation or recovery discs.
The last backup for the desktop was (I think) January 23rd, and with 3-4 people using it, there's a lot of information that we really don't want to lose.

Thanks to anyone who can help.

EDIT:  Using Knoppix, I've successfully recovered all our important files (and more). Windows appears to be fine, I just can't figure out how to get it to boot up. So far I've found files from grub4dos and/or grubutil in the topmost folder of sda1 (the primary hard drive partition), on the desktop (which was where I put them before all this happened), and I think I've seen more other places when I was looking for files to save.

---

