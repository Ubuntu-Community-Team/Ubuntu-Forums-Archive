---
title: "Grub, boot option &quot;Windows 7&quot;"
date: 2010-11-24
forum: General Help
---

### Post by frotscher on 2010-11-24
Hi,

I'm working with Ubuntu 10.04 and want Windows 7 be available as an option in the grub2 boot loader on startup. Therefor I changed the file /etc/grub.d/40_custom in the way I found it in another forum. Its content is now:
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 7" {
insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set 7892E93292E8F612
chainloader +1
}
```and I now also have the option "Windows 7" on startup. Unfortunately the system tells me that the boot manager for this OS is missing when I choose it. The UUID and also *set root = (hd0,1)* are correct.

I assume that I messed up the boot manager by myself because here is what I did:

1. I had a working Win XP.
2. Out of XP I also installed Win 7 and I was able to choose between them.
3. Then I installed Ubuntu from a LiveCD and from now on I had the grub boot loader that allowed me to choose between Ubuntu and Win XP. Win 7 was not available as an option.
**4. I decided to format the partition containing the Win XP installation.**
5. The Win 7 installation is still existing and I now want to add it to the grub2 boot loader.

Possibly I made this impossible by deleting the old and original Win XP installation because there the boot manager was located. Do you know if my Win 7 installation has a boot manager and where I can look for it and if what I should change in the file mentioned above to get it into the grub2 boot loader?

I thank you in advance and hope that I'm able to use my Win 7 installation without reinstallation,

Ralf

---

### Post by oldfred on 2010-11-24
If you had two installs of windows, windows combines the boot loader files from the second install into the first install. 

If you delete the first install, you also delete the boot files for the second install. You need to move the boot flag (active partition) to the second install. You can use windows, gparted, Disk Utility or command line to move boot flag.

You then need to use your windows repair CD to fix the boot of your windows partition. This will only work if the second install is on a primary partition. 

More info:
oldfred's Windows Vista/Win7 repair links:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)

---

