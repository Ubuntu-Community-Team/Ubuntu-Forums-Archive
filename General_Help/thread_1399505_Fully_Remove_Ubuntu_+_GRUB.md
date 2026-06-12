---
title: "Fully Remove Ubuntu + GRUB?"
date: 2010-02-05
forum: General Help
---

### Post by Cam! on 2010-02-05
I need to revert back to my Windows 7-only PC. How do I take off Ubuntu and Grub for good? I remember the last time I carelessly tried deleting the partition, I couldn't boot back into windows.

---

### Post by oldos2er on 2010-02-05
You need to first restore Windows' boot loader, then you can safely delete any Ubuntu partitions.

---

### Post by Cam! on 2010-02-06
> **oldos2er said:**
> You need to first restore Windows' boot loader, then you can safely delete any Ubuntu partitions.

How do I restore the Windows bootloader without having the re-install disc?

---

### Post by oldfred on 2010-02-06
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP(they create the boot sectors differently) but can run check disk.

---

