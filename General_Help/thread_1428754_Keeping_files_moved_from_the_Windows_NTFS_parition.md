---
title: "Keeping files moved from the Windows NTFS parition to the Linux ext-3 partition safe"
date: 2010-03-13
forum: General Help
---

### Post by McWindows on 2010-03-13
Long story short, my Windows had a fatal crash the other day and since I couldn't find the installation disk, I burned the Ubuntu 9.10 disk image to a CD at a friend's place and installed it on one partition of the hard drive. The other partition contained tons of Windows programs and documents in an NTFS system.

Ubuntu is cool and all, but when I finally found the Windows disk, I wanted to reintall it for dual-booting, to use some programs that don't run well in Wine. To keep some documents safe and not waste any CDs, I moved them over to the Ubuntu partition before installing Windows.

As experienced ubuntuists know, the slightly clumsy Windows installer erases GRUB in the process, and it's recommended to install Windows first. So, now I ended up with a working Windows partition and an Ubuntu partition with all of the stored data, which I can access via guest status with the burned CD.

Here's the catch though - as a guest and without Linux properly installed I can't move anything I moved to the Linux partition from the Windows partition back anymore. All the folders have a little X on their top corner.

I'd be glad to reinstall Ubuntu now, but I must know how to keep all that tranferred data safe. Can I keep it there during the reinstallation? Should I install Wubi on Windows and access the stuff through it?

I'd be glad to hear feedback.

---

### Post by amsterdamharu on 2010-03-13
If you want a double boot then you need to re install grub, this is not a big deal since you already have the installation CD of ubuntu.

Boot with the cd and select try ubuntu (live cd mode).

Here are the commands you need to re install grub:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Under 13. Reinstalling GRUB 2 from LiveCD

---

### Post by phillw on 2010-03-13
Hi,

as it is a restore grub after Win, there's also a dedicated thread over here for it --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Regards,

Phill.

---

### Post by McWindows on 2010-03-13
> **amsterdamharu said:**
> If you want a double boot then you need to re install grub, this is not a big deal since you already have the installation CD of ubuntu.

Boot with the cd and select try ubuntu (live cd mode).

Here are the commands you need to re install grub:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Under 13. Reinstalling GRUB 2 from LiveCD

> **phillw said:**
> Hi,

as it is a restore grub after Win, there's also a dedicated thread over here for it --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Regards,

Phill.


Thanks, guys.

---

