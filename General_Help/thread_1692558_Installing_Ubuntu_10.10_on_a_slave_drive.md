---
title: "Installing Ubuntu 10.10 on a slave drive"
date: 2011-02-21
forum: General Help
---

### Post by Habeouscorpus on 2011-02-21
I am going to be installing a dual boot system on my father's computer. (Score!) He has two hard drives in his computer, one of which is windows. The windows partitions are on the master. I want to install Ubuntu onto the slave drive, so that everybody has enough space to work. (And if I goof up, I won't turn his computer into a paperweight.)

1. Will GRUB recognize the windows partitions on another drive and add them to the boot configuration? 

2. Will I have to set the slave drive with Ubuntu and GRUB as the boot device in the computer's BIOS? (I'm thinking yes for that one.)

3. Can anything go wrong? I've already backed up every partiton on the windows drive, and the other drive, so if anything goes wrong, I can restore everything! But it would be nice to have a warning. 

Thank you!

---

### Post by oldfred on 2011-02-21
Because you mention master/slave, I assume its an older system with IDE drives. Newer systems with SATA drives let you use software to choose boot drive (BIOS), but older computers, the BIOS is not smart enough to choose a drive and the boot drive is selected with jumpers on drive or location on a cable select drive.

If IDE, only the primary master is bootable, so you have to let grub install to that drive. It will give you the choice to boot windows or Ubuntu.

---

