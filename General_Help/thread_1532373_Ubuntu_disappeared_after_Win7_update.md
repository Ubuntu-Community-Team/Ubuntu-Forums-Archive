---
title: "Ubuntu disappeared after Win7 update"
date: 2010-07-16
forum: General Help
---

### Post by Lambik on 2010-07-16
I tried to find info about this, but didn't find anything of use.

I recently formatted my computer, installed Vista, upgraded it to Win7 and installed Ubuntu 10.04. Everything worked just fine, but then I had to install some Windows updates. Booted, and got the following error message instead of the grub screen: Error: no such device (number) - Grub rescue >.

I loaded the LiveCD, did sudo update-grub, but again device not found. Apparently, only 1 partition was found, namely my Win7 partition. Fortunately, I could fix the problem with a windows repair cd (bootrec.exe) and I could boot into Windows again.

Strangely enough, Linux seems to have disappeared from my hard disk. My Windows partition is now 150 gig large, which is all of the hard disk...

Does anyone know what caused the problem and how it could or should have been fixed?

---

### Post by Noz3001 on 2010-07-16
You formatted your hard drive when you installed Windows. Everything you had is gone.

---

### Post by WorMzy on 2010-07-16
I've never heard of a Windows update modifying the partition table of a disk. Did you, by chance, install Ubuntu inside the Windows partition as a Wubi installation? Have a look in your "C:\" and see if you have a folder called Ubuntu.

---

### Post by Lambik on 2010-07-16
Hi,

I formatted my computer before installing Windows, and I only installed Ubuntu after installing Windows, but not using Wubi.

---

### Post by WorMzy on 2010-07-16
If that's the case, and now the Windows partition extends across the whole of the disk, then I'm afraid that there's a good chance that your Ubuntu partition and data is lost. You could try using data recovery software to try and recover it, but I can't offer any advice regarding such software.

I think the best thing to do would be to repartition your drive, and reinstall Ubuntu. Just make sure to double check all Windows updates in the future and refuse any that look suspicious.

---

### Post by ELD on 2010-07-16
I've never heard of a Windows Update doing that since no Windows Update ever touches partitions, seems like it's another issue altogether. As others said it seems you will just have to re-install.

---

### Post by Miljet on 2010-07-16
I doubt that the Windows update resized the partitions. Messed up Grub maybe. This is when the partitions got resized: 
> Fortunately, I could fix the problem with a windows repair cd (bootrec.exe) and I could boot into Windows again.

---

### Post by ELD on 2010-07-16
> **Miljet said:**
> I doubt that the Windows update resized the partitions. Messed up Grub maybe. This is when the partitions got resized:

That's 99% going to be the cause and it will restore 100% windows, it doesn't take into account anything else.

I am still unsure how a Windows Update would affect grub though?

---

### Post by bcbc on 2010-07-16
I've lost partitions after booting into windows. for some reason windows doesn't always see things the way ubuntu (and gparted) does. Try using testdisk, it's pretty good at recovering the partition after windows has done it's thing.

I recommend partitioning using the windows tools, that way windows knows about them properly and this probably won't happen in the future. But for now, use testdisk and then at least (hopefully) you can recover what you have.

---

