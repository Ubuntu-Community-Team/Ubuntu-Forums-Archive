---
title: "Boot with nomodeset?"
date: 2011-03-21
forum: General Help
---

### Post by jage on 2011-03-21
When the boot menu comes up for the live CD I can use F6 to set "nomodeset" and that is the only way the live CD will run.

I've used this to install ubuntu 10.10 to the hard drive, there are no other operating systems or partitions (default swap/exf1).  I've installed and reinstalled grub, and grub-install -v gives:
grub-install (GRUB) 1.98*20100004-5ubuntu3

So when I boot from harddisk I need to use nomodeset, and I can't figure out how to do this.  /boot/grub has no menu.lst file and I don't get a GRUB menu, which isn't important except that any instructions I've found are from the GRUB menu.

I can run the live CD, or boot to microubuntu prompt, but from either I don't know how to set my boot or cause a boot with nomodeset.  Command line is fine, but I'd also like to know how to permanently make the HD boot with nomodeset as well in case I can't get a proper driver or whatever once I boot into ubuntu.

---

### Post by Dark_Stang on 2011-03-21
Grub 2 uses /boot/grub/grub.cfg for it's config file.

---

### Post by oldfred on 2011-03-21
Grub does not show menu if only one system is installed. You should be able to hold shift key down from BIOS until menu appears to get menu. Then with e you can edit linux line to add nomodeset.

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)

---

### Post by gmargo on 2011-03-22
> **jage said:**
> how to permanently make the HD boot with nomodeset

Edit the **/etc/default/grub** file.
Look for the **GRUB_CMDLINE_LINUX_DEFAULT** entry.
This probably says "quiet" or "quiet spash".
Add "nomodeset" to this string. (Or replace the string with "nomodeset" - I frankly dislike the "quiet" and "splash" options)
Then run the **update-grub** command.
Reboot.

---

