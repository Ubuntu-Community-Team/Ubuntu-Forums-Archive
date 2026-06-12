---
title: "How do i fix"
date: 2010-04-03
forum: General Help
---

### Post by TheOne159 on 2010-04-03
I installed ubuntu on my laptop and now i wanted to take it off so i started windows vista in safe mode and removed the disk space for ubuntu (I thot would also remove GRUB) 

and now i want to recover my comp to factory settings but the grub loader opens before System Recovery (F11) even opens so in short how do i get rid of the grub loader?!?!?!?

This is what it looks like:

GRUB Loading.
error: no such partition
grub rescue>

---

### Post by oldfred on 2010-04-03
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by gregsmith_to on 2010-04-03
The grub install places code in the master boot record, when booting it loads a config from /boot/grub/grub.cfg, which is probably deleted now. You need to restore the MBR to what it was before you installed grub, maybe if you boot an ubuntu 'LiveCD' and choose the 'recover' option there may be something. I don't think Microsoft can help -- since they basically don't recognize the possibility of other OS on the drive -- other than a full install from a DVD. Perhaps there are utilities to restore the MBR, maybe on one of the 'utility' bootable CDs out there; I've never been in that situation myself.

---

### Post by Naitsirhc Hsem on 2010-04-03
you can boot using the microsoft installer cd.

then go into the recovery console and execute

fixboot and fixmbr

reboot and your master boot record should be windows again

---

### Post by TheOne159 on 2010-04-03
still need help.. i have a preinstalled version of vista..

---

### Post by oldfred on 2010-04-03
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP(they create the boot sectors differently) but can run check disk.

---

### Post by oldos2er on 2010-04-03
I think Super Grub Disk can restore Windows' MBR: [http://www.supergrubdisk.org/index.php](http://www.supergrubdisk.org/index.php)

---

