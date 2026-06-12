---
title: "Problem with dual boot"
date: 2012-01-14
forum: General Help
---

### Post by Kurten on 2012-01-14
Hello linux world!

I'm a bit new to linux but I've been playing around with it for a few days now and have begun migrating from my previous windows environment.

I recently installed Ubuntu 10.04 on my desktop which is a home built machine, the problem is that ubuntu doesn't detect my other hard drives. They are not just unmounted, they basically doesn't exist. I can't find em anywhere. During the installation GRUB couldn't detect any other OS so the GRUB boot loader doesn't work, instead I have to boot manually from BIOS whenever I want to boot windows. What should I do? I want to access my files on my windows disks and i want to be able to use GRUB instead of manually booting via BIOS.

Please help

My current setup
1x 320 GB SATA drive (Windows 7 is installed on this one)
1x 1TB SATA drive (nothing installed here, just a bunch of files)
1X 160 GB SATA (partioned in 2 partions, / and swap)

Motherboard: Gigabyte GA-790FXTA-UD5 with BIOS version F3J

//Kurten

---

### Post by duke.tim on 2012-01-15
Could you post the results of 

```
sudo fdisk -l
```

---

### Post by Kurten on 2012-01-15
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00029469

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18658   149864448   83  Linux
/dev/sda2           18658       19453     6382593    5  Extended
/dev/sda5           18658       19453     6382592   82  Linux swap / Solaris

---

### Post by duke.tim on 2012-01-16
This is quite *perplexing*. I'm going to **_guess_** that this is caused by bios settings.

Here is an idea, boot to a Live Cd (Ubuntu disc -> Use ubuntu without installing option). Can you access your other drives via the live environment?

Oh and can you see the other drives when you are booted into Windows?

---

### Post by Mark Phelps on 2012-01-16
Don't know how new your machine is, but some of the really new ones have SATA III ports on their motherboards -- and Linux distros sometimes are unable to see drives connected to those ports.

As mentioned, you SHOULD be able to see ALL the physical drives when booted into Windows.  If you're running Win7, open the Disk Management tool and there should be a "row" of partitions for each of the drives.

---

