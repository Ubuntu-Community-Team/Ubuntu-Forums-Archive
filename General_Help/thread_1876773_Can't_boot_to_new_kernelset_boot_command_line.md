---
title: "Can't boot to new kernel/set boot command line"
date: 2011-11-06
forum: General Help
---

### Post by nebkor on 2011-11-06
Hello, I'm having trouble figuring out some boot-related issues with my 11.04 install.  First, I've installed, via apt-get, some later 2.6.38-* kernels:

concubine:~> dq -l |grep linux-image |awk '{print $2}'
linux-image-2.6.38-10-generic
linux-image-2.6.38-11-generic
linux-image-2.6.38-12-generic
linux-image-2.6.38-8-generic
linux-image-generic

But, 2.6.38-8 is the only one that boots:

concubine:~> uname -a
Linux concubine 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux


I have no grub/grub2 boot menu on boot, even if I hold down the "shift" button.  I also have no /etc/default/grub file.  I'd like to try the 2.6.38-12 kernel.

The second issue is that I'd like to try adding "ec int r=0" to the kernel boot command line ([http://www.thinkwiki.org/wiki/How_to_make_ACPI_work](http://www.thinkwiki.org/wiki/How_to_make_ACPI_work)), but again, all the documentation seems to pre-suppose the existence of files that I don't have ([https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)).

If anyone knows why installing the appropriate Linux image packages doesn't update the bootable kernel, I'd love to hear it.  Ditto how to set the boot command line.

---

