---
title: "ubuntu inside a windows formatted logical partition"
date: 2011-10-02
forum: General Help
---

### Post by Oxyris on 2011-10-02
So ubuntu won't boot after install (grub won't boot either) and I think it may be because it was installed inside the extended partition. On windows it shows me a logical partition that was smaller than my original and the two linux partitions (actually they have no identifiers like what format they are in or what they are called but it's obvious what they are). When I booted into the live cd, it shows that the logical partition and the linux partitions are technically all under one extended partition. The logical partition is NTFS and I think that creates a conflict with the linux partitions ext4. My question is whether just reformatting the NTFS partition would get grub to show up or whether I should reformat the entire extended partition and reinstall ubuntu? Should I do this in windows disk management or is gparted on the live cd a better option?
Or am I just completely wrong and the problem is something else?

---

### Post by dino99 on 2011-10-02
standard installation:
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by Oxyris on 2011-10-02
> **dino99 said:**
> standard installation:
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

err... maybe I'm wrong but aren't I only allowed to have 4 partitions on a disk? I already have two windows partitions (I would get rid of one of them but I'm not too sure what's inside the first one. think it's the boot partition). or do these 3 linux partitions occur in an extended partition?

---

### Post by Oxyris on 2011-10-02
okay new problem! I'm in the live cd right now and I'm trying to reformat  the extended partition. It won't let me delete the extended partition nor the logical partition and linux partitions within because it's telling me that the i have to unmount /dev/sda5 first (the logical partition is /dev/sda5, the linux and swap follow it).. Going to try disk utility next

---

### Post by JKyleOKC on 2011-10-02
You have to turn swap off after booting from the LiveCD. If Ubuntu finds a swap partition on the drive, it will use it even when booting from the CD, and that makes the partition busy. Search for "swapoff" for instructions on using it; I looked at "man swapoff 8" to give you an example but it wasn't at all clear...

---

### Post by Oxyris on 2011-10-02
> **JKyleOKC said:**
> You have to turn swap off after booting from the LiveCD. If Ubuntu finds a swap partition on the drive, it will use it even when booting from the CD, and that makes the partition busy. Search for "swapoff" for instructions on using it; I looked at "man swapoff 8" to give you an example but it wasn't at all clear...

hmm, i'll try that next. The only thing I managed to get gparted to do was to format the NTFS logical drive into ext4. When I rebooted, it booted straight into windows but this time I didn't get a screen that said the disk was inconsistent like I did before. So I wonder if that means that extended partition is bootable after all...
Also, I typed into terminal to get the list of disks/partitions and only the windows partition came up as boot. In gparted also, the flags said boot but not any of the other partitions. Is it possible that this is why ubuntu won't boot?

---

