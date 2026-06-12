---
title: "Grub problems"
date: 2012-01-12
forum: General Help
---

### Post by StoicalFlame on 2012-01-12
I was formatting my Linux hard drive after trying to use Ubuntu and after I finally finished this showed up. It gives the error unknown filesystem because I changed it to NTFS for the Windows disc I was about to use for a swap of OS. Without Linux or an operating system in general how do I disable grub so I can boot from my windows CD?

---

### Post by bluexrider on 2012-01-12
Put the Windows CD in and start the machine. After the BIOS has passed then hit F8 several times to enter the Windows Recovery.

---

### Post by Mark Phelps on 2012-01-13
> **StoicalFlame said:**
> Without Linux or an operating system in general how do I disable grub so I can boot from my windows CD?

You don't need to!  

When you boot from the Windows CD, your PC doesn't even see GRUB.  Windows will overwrite the MBR, effectively removing traces of GRUB, when it finalizes its install.

If you're still seeing GRUB while booting when the CD is inserted, then you're still booting from your hard drive, NOT from the CD.

---

