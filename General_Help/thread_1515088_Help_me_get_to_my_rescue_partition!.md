---
title: "Help me get to my rescue partition!"
date: 2010-06-21
forum: General Help
---

### Post by BlueNoteMKVI on 2010-06-21
I have an HP DV9810 laptop with dual hard drives, dual-booting Windows Vista and Kubuntu.  Last week when I booted up I got a SMART error that hard drive failure was "imminent."  I pulled out the Windows drive, moved the Linux drive over to the primary slot, reconfigured GRUB and was able to get back to work with Linux only.  So far so good.

Tonight I installed the new hard drive, planning to get Vista up and running again.  I know that on my old drive there's a recovery partition that should allow me to reinstall Vista with all of the necessary drivers (Vista came pre-installed, but no installation CDs were included).  I put the old drive into a USB enclosure and attempted to boot it, but I get GRUB error 17 and can't go any farther.  How can I get past GRUB into the recovery partition?

---

### Post by Ocxic on 2010-06-21
USB drives can be tricky with grub, the best course of action would be to put the drive back into your computer, and copy the recovery partition over to the new drive. then disconnect all your other drives, and do the recovery.

or just download a copy of the Windows installation disk. just make sure your using the same copy (home/pro) as you are on your computer. and you should be able to use the Key that is on the sticker on your computer.

Just be careful, Windows WILL overwrite GRUB what you install it. that is why you need to disconnect all your other drives.


I'm not promoting piracy, the install disk means nothing. It's the Activation Key that matters.

You can also check with HP, and maybe Microsoft to see if you can get recovery/Install disc's. your hard drive failing is something I find that Manufactures don't think of when they create these crappy recovery partitions.

---

### Post by wilee-nilee on 2010-06-21
Get the oem install from HP if you can it will serve you better.

---

### Post by Mark Phelps on 2010-06-22
> **BlueNoteMKVI said:**
> I know that on my old drive there's a recovery partition that should allow me to reinstall Vista with all of the necessary drivers (Vista came pre-installed, but no installation CDs were included).
In general, recovery partitions will reformat the entire hard drive and reconfigure it the way it was when you received the machine -- including erasing any other partitions.  So, if you're going to do the recovery that way, you would not want anything on your new drive when you do it.
>  I put the old drive into a USB enclosure and attempted to boot it, but I get GRUB error 17 and can't go any farther.  How can I get past GRUB into the recovery partition?
Booting from USB is tricky at best -- and simply might not work with your old drive.  I had a similar problem with a drive recently, and nothing I did would get Ubuntu to recognize it when I had it connected via a USB enclosure.  I had to resort to connecting it via Win7 -- it saw the drive and everything on it.

IF it were my system, I would boot from a partitioning CD, connect the old drive via USB, and see if I could copy the recovery partition from the old drive to the new drive.  Then, boot with the new drive installed, and use the recovery option to reinstall Vista. But, I don't know what boot resources you have available.

---

