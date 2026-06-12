---
title: "replace windows boot manager with grub2"
date: 2009-10-15
forum: General Help
---

### Post by kinetic-jw on 2009-10-15
I installed Ubuntu 9.04 through WUBI. I want to replace the Windows boot manager with GRUB2. 

-Is GRUB2 ready for this?
-Is there a special command to install GRUB2? (if not, what is the package name?)
-What are the differences between the GRUB2 conf file and the GRUB1 conf file?

 Thank you for your time.

---

### Post by mike555 on 2009-10-15
If you installed Ubuntu as Wubi , it's inside Windows and needs to use the Windows boot........

---

### Post by kinetic-jw on 2009-10-15
> **mike555 said:**
> If you installed Ubuntu as Wubi , it's inside Windows and needs to use the Windows boot........

Why would GRUB not work? Stage 2 could still be in /ubuntu/boot/, is it really hardcoded where it is? Or is it another reason?

Even the Windows website says that 'various programs in some linux distributions' could replace thier boot manager if need be.

---

### Post by mike555 on 2009-10-16
a wubi install is inside Windows , not on a separate partition , more like a virtual section inside a folder.

---

### Post by dandnsmith on 2009-10-16
If you look at [this thread](http://ubuntuforums.org/showthread.php?t=1290851) you'll find useful reference stuff for grub2 differences and config.

HTH

---

### Post by P4man on 2009-10-16
AFAIK, grub can not be installed upon NTFS volumes, you would need at least a FAT or Ext partition to install grub unto. Further more, grub won't be able to boot your ubuntu wubi install, as it resides on ntfs (inside a virtual file system), so all grub can do is chainload the windows bootloader... which begs the question why you'd want to do this at all.

---

