---
title: "Changing partitition useage and GRUB."
date: 2006-02-02
forum: General Help
---

### Post by Snoopy2052 on 2006-02-02
I tried a trial (yes, three OSs) boot system for a while, when I was getting used to Linux, and so I have a number of partitions:

Windows, Windows data, Suse, Ubuntu and Swap (I think, in that order; windows data is an extended partition, if that's worth much). 

I've now decided I'm happy with Ubuntu for my Linux fix at the moment, and am looking to get rid of Suse and replace that partition with the /home directory. However, I installed Suse after Ubuntu, and so the GRUB screen is the Suse one. If I just format the partition and mount it as the /home directory for Ubuntu, will GRUB care? If it will, what should I do to fix it?

Many thanks in advance,
Snoopy

---

### Post by el3ktro on 2006-02-02
I'm not entirely sure, but running "sudo dpkg-reconfigure grub" within your Ubuntu install should do the trick. Choose to install Grub in the MBR, and it should set all paths correctly.

Tom

---

### Post by cotcot on 2006-02-02
As you have installed Ubuntu before Suse you have the grub menu.lst, stage 1, 1.5 and 2 in your ubuntus /boot/grub.
It is enough to boot ubuntu and to do a grub-install. The grub install will overwrite the bootloader in the MBR (the one you made during Suse install).
There is in this forum somewere a howto to move /home from the root partition to a separate partition.

---

### Post by Snoopy2052 on 2006-02-03
Excellent, thanks guys. I'm fairly sure I can cope with the moving /home over to a separate partition, but I was a bit worried about messing with GRUB and suddenly having a system that wouldn't boot anymore!

---

