---
title: "What the trick to use Compact Flash as a drive?"
date: 2010-05-29
forum: General Help
---

### Post by bakegoodz on 2010-05-29
I have a project were I have been trying to use Compact Flash (CF Card) was a Ubuntu system drive, but can't seem to successful partition it. I can partition without error, but I go back into the partition tool it gives usually a cryptic error about the partitions. They won't format either. For example Gparted puts orange triangles next to each partition. cfdisk says partition exceeds cylinder boundary. I've tried three different computer, two different CF to IDE adapters (a laptop and desktop type) and four different models/brands of CF cards all are supposed to fixed disk IDE compatible.
My theory is the drive geometry is not being detected correctly, or maybe a sector alignment issue. I've tried GUID partitions too and it doesn't help.
How do I correctly partition a CF card?

---

### Post by Joe of loath on 2010-05-29
Have you tried fdisk? I've had problematic SD cards before, and fdisk is the most flexible. I also find it rather intuitive, but that's just me.

---

### Post by bakegoodz on 2010-06-19
I was trying to use a CF to IDE as an inexpensive SSD in an old laptop, since IDE SSDs are disappearing and are very expensive if you find one. What I found that BIOS boot support stinks for CF, even tough CF is supposed to be all IDE based and compatible, bla, bla, bla. I finally got a desktop to work with it, if I turned DMA to PIO mode in the IDE config, the laptop didn't have that option, so I gave up and put a hard drive in it. 
The good news is if you want to do a CF to SATA, it worked very well for me. The CF to Sata have a bridge chip on them make the compatibility problems go away, at lest with Addonics adapter with a Marvell bridge chip I have.

---

