---
title: "Uninstall Questions"
date: 2010-05-01
forum: General Help
---

### Post by Ethan G. on 2010-05-01
Hey- So I normally dual-boot Ubuntu and Windows 7, but I recently had to wipe my hard drive and install Ubuntu 10.04 on the whole disk (it was quite the SNAFU for a few days). I would like to continue dual-booting, but when I go to reinstall Windows on my machine using the recovery disks, it doesn't recognize the hard disk to install it on, though. Needless to say I'm confused. Is there any way to partition the drive from Ubuntu so I can install Windows on that partition? Any help would be appreciated.
Thanks,
-Ethan

---

### Post by Andreas1 on 2010-05-01
i think you have to create at least one windows-formatted (ntfs or fat32) partition for the windows installer to recognize. you can do that with grub from a live cd. not sure though, i never tried that.

by the way, once you installed windows, it will remove grub and you won't be able to boot ubuntu, then you'll have to restore grub from a live cd, just google that, there are a few howtos for that.

---

### Post by spuny on 2010-05-01
you can partition your hard disk using gparted program. Run terminal and type gparted if it's not installed, install it and partition your hard disk. Make sure that the partition you are going to be using is in NTFS format.

---

### Post by cgoo on 2010-05-01
Go to System > Administration > GParted
Create an ntfs partition to install Windows to. You will likely need to reinstall grub2 after installing windows.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by Ethan G. on 2010-05-02
I partitioned my drive with an NTFS partition and the Windows recovery discs still wont recognize it, but at this point it seems more like a Windows issue than a Ubuntu one. Suggestions? Will a Windows install CD work better than a recovery disc? Thanks for the help so far!
-Ethan

---

### Post by zeroseven0183 on 2010-05-02
> **Ethan G. said:**
> I partitioned my drive with an NTFS partition and the Windows recovery discs still wont recognize it, but at this point it seems more like a Windows issue than a Ubuntu one. Suggestions? Will a Windows install CD work better than a recovery disc? Thanks for the help so far!
-Ethan

I believe so. Windows installation CD works better. But If I were to dual-boot, I would install Windows first then Ubuntu. 

Here are some detailed suggestions how to dual boot, install Windows after Ubuntu, install Ubuntu after Windows: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Always be sure you back-up your files before messing with your partitions.

---

### Post by Andreas1 on 2010-05-02
> **Ethan G. said:**
> I partitioned my drive with an NTFS partition and the Windows recovery discs still wont recognize it, but at this point it seems more like a Windows issue than a Ubuntu one. Suggestions? Will a Windows install CD work better than a recovery disc? Thanks for the help so far!
-Ethan

it's hard to tell, some recovery discs are very unflexible. for example i have an acer laptop and recovery disc only works if there is an FAT32-formatted partition, doesn't work with ntfs, but that's because acer is crap.
two further things come to my mind: *primary* partition, and *boot flag* on the partition. don't know if either could be a requirement, maybe someone more experienced with windows can help...

---

