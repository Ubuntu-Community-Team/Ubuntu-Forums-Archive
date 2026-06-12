---
title: "partitioning with BTRFS"
date: 2011-03-15
forum: General Help
---

### Post by MCSE_Crossover on 2011-03-15
Ok...I'm just diving in to figuring out how to partition/utilise BTRFS.

I am used to just installing with EXT4 and carving out a / and a /home

But, from what I understand, this isn't the case with BTRFS?

I know you have to create a separate /boot as grub doesn't support the file system.

But, with BTRFS, we just create a / and /home and others would then just be subvolumes?

What happens if I want to reinstall? I have liked being able to just wipe / and reinstall the OS, leaving my personal files in tact. Does this still happen if the /home is just a subvolume? Hopefully that makes sense!

The more detailed answer, the better! I appreciate all your help!

---

### Post by oboedad55 on 2011-03-15
What do you mean by "subvolume"? If you don't reformat /home then you won't lose anything. And it's true that at this point Grub doesn't like btrfs so you'll need a small /boot partition with ext4 or whatever.

---

### Post by cbowman57 on 2011-03-15
Based on my end-user experience.

Pros: Compression & Defragmentation

Cons: Imaging software (i.e. Clonezilla) operates in raw mode.

Other than that, oboedad55's comments & questions apply.

---

### Post by ankspo71 on 2011-03-16
> **MCSE_Crossover said:**
> 
But, with BTRFS, we just create a / and /home and others would then just be subvolumes?

What happens if I want to reinstall? I have liked being able to just wipe / and reinstall the OS, leaving my personal files in tact. **Does this still happen if the /home is just a subvolume?** Hopefully that makes sense!


Hi,
I'm not sure what to do in the event you need to reinstall a BTRFS system again. I imagine you need to make a backup (not snapshot) of your home folder to a CD or USB stick so you can reformat the hard drive. I would think that reformatting your BTRFS partition would wipe out all subvolumes too. BTRFS is supposed to help eliminate the need for reinstalls though, because it provides a way to keep snapshots of the system.

As for reinstalling because you no longer want to use BTRFS:
As far as I know, there is no way to convert from BTRFS to an older filesystem type (ext3, ext4, etc), and subvolumes are only relevant to BTRFS. So if you format your hard drive into BTRFS and then later you decide not to use BTRFS anymore, you need to make a backup (again, not snapshot) of your home folder so you can reformat your partitions. After Ubuntu is reinstalled you can restore those files and settings back to your newly created /home partition.  

Yes, you are correct, Ubuntu will not be able to start if /boot is formatted as BTRFS.

[https://help.ubuntu.com/community/btrfs](https://help.ubuntu.com/community/btrfs)

Hope this helps.

---

