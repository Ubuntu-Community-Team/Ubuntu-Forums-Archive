---
title: "System can't see SATA drive after power failure."
date: 2010-11-15
forum: General Help
---

### Post by serutan on 2010-11-15
I'm embarrassed to say I accidentally cut the power to my file server (hardy heron) while it was rebooting. Now it doesn't recognize the SATA drive. It boots fine, as the OS is on another disk, but it says the SATA doesn't exist. The SATA disk is specified in fstab as:

# /dev/sdd1
UUID=5d4b8976-6b3b-44ab-91dc-24004ed7906f /media/big0   ext3   defaults    0   2

During boot the automatic fsck fails saying it cannot resolve the UUID. 
What I've tried so far:

mount -a says "special device ... does not exist." 
Trying to mount by UUID and /dev/sdd1 says the same thing.
fsck and e2fsck both say the superblock cannot be read or is not correct.
(which doesn't mean it's seeing the disk; fsck /dev/whateverdude says the same)
blkid lists the other disks but not the SATA.
gparted lists the other disks but not the SATA. 
partprobe displays no messages and doesn't seem to have any effect. 

Nothing has physically changed. The data cable is solidly connected at both ends and the SATA controller is well seated in the PCI slot. The drive body gets warm when the computer is running, so it definitely has power. 

Why can't Linux see the SATA disk?

---

### Post by TeoBigusGeekus on 2010-11-15
Try with a live cd.
Also, open the box and disconnect/reconnect your hard drive (from both ends, drive+mb). Take out and reattach its power supply as well.

---

### Post by foureyesboy on 2010-11-15
Looks like the OS doesn't see the hard drive at all.

Have you checked the BIOS setting of the machine and the setting of the SATA controller card if anything was revoked to factory default (say, IDE compatible mode vs AHCI, etc.)?

During the bootup, do you see the hard drive showing up during the BIOS scan?

If the hard drive isn't shown during the BIOS scan and you're sure the BIOS and controller settings are correct, you mean need to try re-seat the SATA controller.

---

### Post by serutan on 2010-12-01
Thanks for the valuable info, and I'm sorry to take so long replying. After unplugging the SATA controller, rebooting normally, then plugging it back in and rebooting with the LiveCD, I was able to see the drives. I have reconstructed fstab so everything seems to be peachy now. Still no idea what actually went wrong, but oh well!

---

