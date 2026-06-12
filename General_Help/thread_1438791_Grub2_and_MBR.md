---
title: "Grub2 and MBR"
date: 2010-03-25
forum: General Help
---

### Post by dld on 2010-03-25
There has been a lot written about Grub2, and I have not read all of it, but enough to guess that my problem has an answer that is easy for someone.  I had problems upgrading to 9.10 a while back, and ended up installing a second copy on a large unformatted chuck of my HD.   The other day I thought I might update that second version.  All fine, except that now my Grub2 menu is provided by that second copy.  My primary version has a /boot partition, /home partion, etc.  The second copy has everything under / in one partition.  Something written to the MBR?   How do I put my primary version in charge of Grub2 again?
   Don

---

### Post by srs5694 on 2010-03-25
Boot to the version you want to use and type "sudo grub-install /dev/sda" in a shell window (Terminal, xterm, Konsole, etc.). This will re-install GRUB to the MBR of your first hard disk (assuming it's /dev/sda and not /dev/hda; change that if necessary).

---

### Post by andrewthomas on 2010-03-25
> **srs5694 said:**
> Boot to the version you want to use and type "sudo grub-install /dev/sda" in a shell window (Terminal, xterm, Konsole, etc.). This will re-install GRUB to the MBR of your first hard disk (assuming it's /dev/sda and not /dev/hda; change that if necessary).
This will work until you get another kernel update on the secondary   install.  Then you will be right back in the same boat.  I believe that   you need to also install the secondary's grub to its partition. 
Maybe someone will suggest an easier way, but you may have to uninstall  grub  and grub-pc (**from synaptic in** **your secondary install**)  then immediately  reinstall and then choose to install to only the  secondary's root partition (make sure you know the right partition) and**  not** the MBR. It will give you a warning suggesting that it is not  the best thing to do, but oh well.
 But for the time being, I would just let it be after reinstalling grub from  your primary and don't add any new kernels or update-grub from your secondary until you have a more definitive answer here.

---

### Post by dld on 2010-03-25
grub-install did the trick!!  Thank you very much.  I will keep an eye on this thread for suggestions until its time to bring up 10.4.
   Don

---

