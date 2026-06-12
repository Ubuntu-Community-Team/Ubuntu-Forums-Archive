---
title: "Booting Windows 7 Breaks GRUB"
date: 2010-07-04
forum: General Help
---

### Post by Darkness Des on 2010-07-04
Every time I use GRUB to boot into Win7, I can't reboot back into GRUB or Windows. I think Windows is forcing itself into the MBR then proceeding to corrupt it. I believe I can just boot into a Live session use "sudo grub-install /dev/sda", but that seems like a lot of work just to reboot. Any suggestions?

---

### Post by oldfred on 2010-07-05
Windows has some software that writes into the MBR which is reserved for booting:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
In Windows 7, I had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
See section 11
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

