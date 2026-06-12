---
title: "Partition New Hard Drive ..."
date: 2006-02-10
forum: General Help
---

### Post by wannabelinuxconvert on 2006-02-10
Hi,

I just got my hands on a new external USB 40gb hard drive ... only thing is its formatted as HFSPlus as my dad bought it for his Mac.

Is there a graphical partition/format program that is included in the standard installation of Breezy as I've just moved house and haven't got broadband setup just yet.

I'm not a guru by any standards, so just need something really easy so I can format the drive to ext3 and make it into two 20gb partitions.

All help will be greatly appreciated as always guys.

Mic

---

### Post by Zeroangel on 2006-02-10
No, but you can install one (GParted) via the Applications -> Add applications menu (its under System Tools). If you can't find it in 'Add Applications' just do a search for it in Synaptic.

Mine works just fine.

---

### Post by yota on 2006-02-10
If you absolutely need a gui you can have a look at gparted, it's really nice and featureful, but it's not part of the standard installation.
By the way making an ext3 fs from a shell is not a guru's task:

```

sudo mkfs.ext3 /dev/sdXX

```

will do it, just replace XX with your disk/partition; assuming that you have ide drives and just one usb disk plugged it should be "/dev/sda1".
To be sure you can issue a "dmesg |tail" just after you plug the disk to see what device node has been assigned to the periferal.
BEWARE: you HAVE to be sure or you can wipe out important data, /dev/sda1 it's the first partition (1) of your first (a) scsi hard-drive and if you have sata drives your os is probably there...

---

