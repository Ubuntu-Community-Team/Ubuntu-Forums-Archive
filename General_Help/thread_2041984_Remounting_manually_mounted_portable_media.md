---
title: "Remounting manually mounted portable media"
date: 2012-08-13
forum: General Help
---

### Post by NekoMaster on 2012-08-13
It seems the only way Im going to get my linux applications running of my FAT32 flash drive or NTFS portable HD is if I mount them manually with the executable bit's enabled.

Though the problem with mounting things manually through FSTAB is that portable media won't remount properly after they've been removed, preventing the user from accessing the drive (and receiving an error about the drive being inaccessible)

So is there a way to manually mount a FAT32/NTFS portable drive in Ubuntu and have it remount properly after its been removed?

---

### Post by bchurchill on 2012-08-14
I'm having trouble understanding your question.  Yes, to run linux applications to execute bit must be set.  If I recall correctly, this always happens when you mount FAT32 or NTFS partitions.  

Typically I don't use /etc/fstab to mount anything other than drives that are always present.  Normally after I plugin a drive I run "sudo fdisk -l" to find the name of the drive, e.g., "/dev/sdc1".  Alternatively, "dmesg | tail" might tell you what the new device is.  Then I create a mount point, e.g., "sudo mkdir -p /media/mydrive", and them mount it with "sudo mount /dev/sdc1 /media/mydrive".  Does that help?

---

