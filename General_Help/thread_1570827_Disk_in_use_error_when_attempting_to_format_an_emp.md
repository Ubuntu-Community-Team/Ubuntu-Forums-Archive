---
title: "Disk in use error when attempting to format an empty partition"
date: 2010-09-08
forum: General Help
---

### Post by andymcca on 2010-09-08
Hey all,

Just ran into a problem involving mdadm, a disk which had been in a raid array, and an attempt to reformat.

Basically, I went to reformat some partitions which had been in raid, and one of them threw the error
andy@andy-desktop:~$ sudo mkfs.ext3 /dev/sdb5
mke2fs 1.41.11 (14-Mar-2010)
/dev/sdb5 is apparently in use by the system; will not make a filesystem here!

An attempt to umount revealed it was not mounted. lvdisplay and fuser did not reveal anything to me, so I just started looking around. I was graphically navigating /dev and noticed a /dev/md_d0 which did not look like /dev/md_d1 etc (it was missing a little arrow). I had not seen this notation before (my raid was md0), but figured it couldn't hurt to try stopping it.

andy@andy-desktop:~$ sudo mdadm --detail /dev/md_d0
mdadm: md device /dev/md_d0 does not appear to be active.
[B]andy@andy-desktop:~$ sudo mdadm --stop /dev/md_d0
mdadm: stopped /dev/md_d0[/B]

**After this, the partition formatted fine!**

I saw a lot of instructions including zeroing the partition and removing a logical volume, but the above was the only thing which worked for me! Just posted it in case it helps someone else. I know I've not been terribly technical!

Any input on exactly what happened (in very simple terms) would be appreciated, though!

-Amdy

---

### Post by dcstar on 2010-09-09
> **andymcca said:**
> 
.........
Any input on exactly what happened (in very simple terms) would be appreciated, though!


You had a device that the system still had configured as being used in a RAID array, and it (rightly) refused access to it while it was still in that configuration.

---

### Post by andymcca on 2010-09-11
> **dcstar said:**
> You had a device that the system still had configured as being used in a RAID array, and it (rightly) refused access to it while it was still in that configuration.
Hmm, this does seem likely... I had issues with md0 not loading on startup. It seemed like mdadm was loading one of my raid partitions, but not the  other one (which is odd because I formatted them the exact same way,  with exactly the same flags, on identical disks). I had tried to set the partition to "raid" with the flags in gparted, but aparently this is something other than setting the partition to type "fd" in fdisk?

Anyway, I could not mount md0 until I used fdisk to set each partition to type "fd" (they were still "83"!).
Is this the intended gparted behaviour and I was just misinterpreting what the "raid flag" was?

After setting the partitions to type "fd", I still had to add the arrays/devices to mdadm.conf before they would successfully mount on startup. Was I missing some key component to having them be automatically detected without using mdadm.conf? It seems like others talk about this.

Oh, and as a final note, (before using fdisk directly) I had the problem again and discovered that mdadm was re-loading the partition as soon as gparted made it. If I ran mkfs.ext4 instead of trying to use gparted the filesystem was created without interference from mdadm (after stopping what mdadm had loaded, of course). Seems odd..

---

