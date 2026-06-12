---
title: "how to copy a partition"
date: 2011-08-19
forum: General Help
---

### Post by pdlethbridge on 2011-08-19
Is there anyway to copy a drive that has a working Ubuntu OS such as on sda1 and put it on sda 7 or 8 of the same hard drive
What I want to copy is my first of 4 primary partitions sda1 and put it on a logical drive on my extended drive and be able to boot from them
 My hard drive has 2  15 gig primary partitions set up for ubuntu and kubuntu on sda1 and sda2. sda3 is a 2gig swap, while the last partition sda4 is  extended it has several 15 gig logical partitions for more ubuntus

---

### Post by haqking on 2011-08-19
> **pdlethbridge said:**
> Is there anyway to copy a drive that has a working Ubuntu OS such as on sda1 and put it on sda 7 or 8 of the same hard drive
What I want to copy is my first of 4 primary partitions sda1 and put it on a logical drive on my extended drive and be able to boot from them
 My hard drive has 2  15 gig primary partitions set up for ubuntu and kubuntu on sda1 and sda2. sda3 is a 2gig swap, while the last partition sda4 is  extended it has several 15 gig logical partitions for more ubuntus

[www.clonezilla.org](www.clonezilla.org)

---

### Post by pdlethbridge on 2011-08-19
I opened up place and then opened computer when I right clicked file system it then allowed me to open up brasero, with a 1.6 gig project size. Which would have been an iso

---

### Post by oldfred on 2011-08-19
You have to reinstall grub2's bootloader to the MBR, you also have to edit fstab in both installs with the new locations. After all the updating, it is almost easier just to reinstall and then copy /home over so you have your current settings & data.

---

### Post by pdlethbridge on 2011-08-20
Your right after all again just easier to put a new install on a different partition. Start up manager will all ways give me a choice to boot from and there is  a choice at the very beginning of the boot process

---

### Post by Rebelli0us on 2012-05-26
> **oldfred said:**
> You have to reinstall grub2's bootloader to the MBR, you also have to edit fstab in both installs with the new locations. After all the updating, it is almost easier just to reinstall and then copy /home over so you have your current settings & data.

Thank you. Is it really that simple? You can clone your profile by just copying */home* to a fresh install?

---

