---
title: "GRUB on dedicated partition (auto populate)"
date: 2010-07-25
forum: General Help
---

### Post by ninocass on 2010-07-25
Hi All

Im running VMware fusion on my mac book pro and i want to boot my physical ubuntu partition.  After wasting hours trying to add the partitions directly into vmware grub complained that it couldn't find the correct partition.  

I abandoned that avenue and created a 50MB vmware partition and installed GRUB2 on it so in the VMware i then attached the 50MB grub partition and the 250G physical drive.  This all works fine however i cant seem to get GRUB2 to automatically populate the menu.  

On the GRUB2 partition i have /boot/grub/* and /etc/grub.d/ * and in the grub.cfg i have set GRUB_DISABLE_OS_PROBER=false

however when i run update-grub i get an error saying something like "mkconfig-grub cannot find / is dev mounted?"

i can manually run /etc/grub.d/30_os-prober and it prints out a list of all my partitions which i can paste into grub.cfg however i dont want to have to manually do this for each kernel upgrade.

Im doing all this via a 10.04 live CD.

Many Thanks 

Nino

---

### Post by aprekates on 2010-12-19
I have similar questions and i send [a question]("http://lists.gnu.org/archive/html/help-grub/2010-12/msg00014.html") to help-grub mailling list.
So if keep an eye there if still interested or curious.

My first guess is that grub-update will always take as input configuration files-scripts that reside in the same partition as the os you're working.

---

### Post by sefs on 2010-12-19
When you install Grub2 on a dedicated partition I think you have to manually create entries in grub.cfg yourself.

Please reference this thread... [http://ubuntuforums.org/showthread.php?t=1585598](http://ubuntuforums.org/showthread.php?t=1585598)

---

