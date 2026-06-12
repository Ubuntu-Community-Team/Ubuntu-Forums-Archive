---
title: "Sharing partition"
date: 2010-02-02
forum: General Help
---

### Post by thermobee on 2010-02-02
Is it possible to create a sharing partition after i have already installed both ubuntu and xp? I have an acer aspire one netbook and ive been using it with ubuntu for about a year now.

---

### Post by oldfred on 2010-02-02
If you have space it is possible. You may be able to copy data from windows and shrink it, then create a new NTFS partition for sharing. I put all my photos, firefox profiles & thunderbird profiles in the shared partition so all my data is the same for both.

[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)

Always backup for editing partitions, you need to use gparted from a liveCD as your partitions cannot be mounted.

Adding a partition should not change existing sda or UUID's but sometimes it does. If so then you have to reinstall grub, and possibly edit fstab.

In XP houseclean and defrag twice before shrinking. You need to leave 10-20% free space or it will run real slow or stop working.

---

### Post by thermobee on 2010-02-02
> **oldfred said:**
> If you have space it is possible. You may be able to copy data from windows and shrink it, then create a new NTFS partition for sharing. I put all my photos, firefox profiles & thunderbird profiles in the shared partition so all my data is the same for both.

[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)

Always backup for editing partitions, you need to use gparted from a liveCD as your partitions cannot be mounted.

Adding a partition should not change existing sda or UUID's but sometimes it does. If so then you have to reinstall grub, and possibly edit fstab.

In XP houseclean and defrag twice before shrinking. You need to leave 10-20% free space or it will run real slow or stop working.
Any guides on how to do that? It seems like the link you gave me is just for sharing firefox profiles and such. I actually want to share around 40gb. Does it matter which OS i get it from?

---

### Post by oldfred on 2010-02-03
Some of these links may be older but the process is the same and screens usually have only changed slightly.

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
With add'l info on manually partitioning
[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Vista and Partitioning - details
[http://www.multibooters.co.uk/partitions.html](http://www.multibooters.co.uk/partitions.html)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

---

