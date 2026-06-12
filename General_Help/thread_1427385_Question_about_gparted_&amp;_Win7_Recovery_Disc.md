---
title: "Question about gparted &amp; Win7 Recovery Disc"
date: 2010-03-11
forum: General Help
---

### Post by Gegenzeit on 2010-03-11
Hi,

I'm three weeks in my Linux experiment and: I want to repartition my disc. One step is to shrink my Windows partition from 900 GB to 75 GB. As far as I know there is a good chance this will

**a)** Ruin my windows' boot procedure
**b)** Ruin the system as a whole

**To a)** I read that the WIN 7 recovery disk is able to repair the broken Windows installation. As this will kill Linux from the start up list (MBR?), I want to use Super Grub Disc to repair this. **Q1**: Is this likely to work?

**To b)** I would not mind to completly reinstall my system, if I had to. But I remember reading something like the Windows recovery disc is not able to set up a system from a scratch, but relies on files on the disc for reinstallation. **Q2**: Is it true and does this mean I won't be able to set up a new Windows partition, if my system crashed complety?


Thanks

Jörg

---

### Post by srs5694 on 2010-03-11
> **Gegenzeit said:**
> Hi,

I'm three weeks in my Linux experiment and: I want to repartition my disc. One step is to shrink my Windows partition from 900 GB to 75 GB. As far as I know there is a good chance this will

**a)** Ruin my windows' boot procedure
**b)** Ruin the system as a whole

Those are indeed risks.

> **To a)** I read that the WIN 7 recovery disk is able to repair the broken Windows installation. As this will kill Linux from the start up list (MBR?), I want to use Super Grub Disc to repair this. **Q1**: Is this likely to work?

First, in my experience Windows is much more likely to become unbootable if you change the *start* location of its boot partition than if you change the *end* location. Thus, if you want to shrink the Windows partition by moving its end point without changing its start point, you'll probably be OK and won't need to recover anything at all.

If a Windows repair renders Linux unbootable, you can recover by re-installing your boot loader (GRUB for Ubuntu 9.04 and earlier, GRUB2 for 9.10 and later). If you're prepared for this by having a suitable emergency disk handy, recovery shouldn't be too difficult. I don't know offhand if the latest Super GRUB Disc includes GRUB2 support, so check on that if you're using Ubuntu 9.10 or later.

> **To b)** I would not mind to completly reinstall my system, if I had to. But I remember reading something like the Windows recovery disc is not able to set up a system from a scratch, but relies on files on the disc for reinstallation. **Q2**: Is it true and does this mean I won't be able to set up a new Windows partition, if my system crashed complety?

I don't believe that's true (certainly I've restored many Windows' systems using install/recovery discs), although there is a caveat. Some (perhaps most) hardware manufacturers have gotten so incredibly cheap that they no longer spend the $0.10 required to provide Windows installation/recovery discs with their hardware. Instead, they put the equivalent on hard disk partitions, assuming that you'll be able to boot the recovery partition to repair damage. If this is the case, there should be a Windows utility you can run to create your own recovery DVD(s). Run it, and make copies of the DVDs you create. (Recordable DVDs aren't as reliable as pressed ones, so it's always best to have a backup of something as important as an OS recovery DVD.) Instead of twiddling your thumbs while this utility burns DVDs, write a letter to your computer manufacturer to complain about how inexcusably cheap they are.

You might also want to consider using Windows backup software to back up your installed system. This will be especially valuable if you've spent much time customizing your Windows system. Be sure to read whatever instructions are provided for *restoring* the system, too; a backup is useless if you can't restore it. I've recently been using [DriveImage XML](http://www.runtime.org/driveimage-xml.htm) for this, although I've only restored once. Note that most of these tools require a Windows boot CD/DVD or at least a basic Windows installation to restore. You can restore a backup made by Linux's ntfsclone utility from Linux, but it will likely only be bootable if the restore partition begins at exactly the same point as the original. It will also only be restorable if the restore partition is as large as or larger than the original, so it won't really be useful for your immediate purpose, although it might be useful for more things in the future.

---

### Post by redbook4574 on 2010-03-11
> **Gegenzeit said:**
> Hi,

I'm three weeks in my Linux experiment and: I want to repartition my disc. One step is to shrink my Windows partition from 900 GB to 75 GB. As far as I know there is a good chance this will

**a)** Ruin my windows' boot procedure
**b)** Ruin the system as a whole

**To a)** I read that the WIN 7 recovery disk is able to repair the broken Windows installation. As this will kill Linux from the start up list (MBR?), I want to use Super Grub Disc to repair this. **Q1**: Is this likely to work?

**To b)** I would not mind to completly reinstall my system, if I had to. But I remember reading something like the Windows recovery disc is not able to set up a system from a scratch, but relies on files on the disc for reinstallation. **Q2**: Is it true and does this mean I won't be able to set up a new Windows partition, if my system crashed complety?


Thanks

Jörg

I have shrunk windoze partitions many times without problems (but make sure you back up first). Try shrinking the partition with windoze own disk management then use the free space to install ubuntu. If as you say you have 900 gb available I would suggest 200 gb for Windoze, 200 Gb for ubuntu and an NTFS data partition readable by both systems.

---

### Post by Jose Catre-Vandis on 2010-03-11
+1 to using the Windows Disk Management Console to do the resizing of your windows partition, and strongly recommend you leave the partition where it is (but do resize if needed), unless you want to carry out a full reinstall. Suggest not to use gparted for W7 partition resizing. Just my TPW.

---

