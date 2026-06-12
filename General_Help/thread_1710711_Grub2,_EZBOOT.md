---
title: "Grub2, EZBOOT"
date: 2011-03-20
forum: General Help
---

### Post by HuckBerry on 2011-03-20
I've long been looking for a way to make an ISO out of a CD I have, write it to a partition and boot it with grub2. I understand that doing that is non-trivial so I decided to go a different route (for now).

I extracted the contents of the CD (iso9660) onto a NTFS partition (/dev/sda6). The CD has several things on it, it first loads a text-based screen that has options to either boot the first HDD, boot to a Windows PE environment, or boot some isolinux-based utlities.

I've observed the following on in its root directory:
/boot/BCD
/boot/bootsec.exe (and others)
/ezboot/*.ezb
/isolinux/isolinux.bin (and others)
/bootmgr

So based on what I see when I boot the CD, and the files I'm seeing on it, the EZboot loads first, then either the Windows PE bootloader or ISOLinux depending on what you pick. 

I have grub installed onto it's own dir and it works fine for linux. When I ran grub-mkconfig it found a Windows Bootloader on /dev/sda6 but when booting to it the machine resets.

So the Question is: Can I chainload EZBoot? If not, can I chainload Windows PE and add a menuentry for ISOLinux?

---

### Post by HuckBerry on 2011-03-21
Additional Information that I've figured out in the last 24 hours:

if I go to the grub2 command line and execute the following:
search --no-floppy --fs-uuid --set (UUID of /dev/sda6)
chainloader (hd0,6)/EZBOOT/LOADER.BIN
boot

The screen goes blank and the machine resets. From what I've read about EasyBoot the loader for the CD looks for /EZBOOT/LOADER.BIN and that sets the process going from there. Since this isn't working I'm assuming that there's something more I have to tell grub.

Will post more when I find more.

---

