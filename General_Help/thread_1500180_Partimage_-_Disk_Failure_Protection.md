---
title: "Partimage - Disk Failure Protection?"
date: 2010-06-02
forum: General Help
---

### Post by slalomchip on 2010-06-02
I'd like to protect myself from a total disk failure.  I'm running Ubuntu 10.4.  Partimage works well for a single partition.  But there appear to be two more partitions on the hard drive, and I'd like recommendations on what I need to do to make sure I'm completely protected.

Partimage idenifies the following three partitions:

sda1 is an "ext3fs" partition of 142.96 GBytes
sda2 is an "-extended-" partition with no specified size
sda5 is a "swap(v1)" partition of 6.09 GBytes

I've successfully backed up sda1 with Partimage.  What else do I need to do to make sure I can adequately restore to another hard drive in the event of a drive failure?

Thanks.

---

### Post by Mark Phelps on 2010-06-03
My preference for backup apps is Clonezilla.  It provides the option of backup up the entire drive -- including all partitions -- in one easy operation.

---

### Post by slalomchip on 2010-06-06
Thanks for the reco on Clonezilla.  I have the following to offer for Clonezilla.  I installed the Ubuntu Alernative version [clonezilla-live-20100521-lucid.zip]("https://sourceforge.net/projects/clonezilla/files/clonezilla_live_alternative/clonezilla-live-20100521-lucid.zip/download") to a USB flash drive.  I had to modify the makeboot script (per the install reco) to -fs instead of -f.  Installed fine.  Tried several times to save the cloned image to as esata drive, bit kept failing after the bitmap even though Clonezilla recognized the esata drive.  Finally I tried the USB drive in USB mode instead of esata mode and Clonezilla performed beautifully (I think - I have not yet tried a Restore).

Anyway - thanks for your reco to use Clonezilla

---

