---
title: "ext4 partition size mismatch"
date: 2011-05-03
forum: General Help
---

### Post by emorkay on 2011-05-03
Hi,

I have created a partition of size 400GB in my 1TB external hard drive and the rest as another partition. Both are formatted as ext4 using Gparted. The reserved block count has been set to 0% using tune2fs. When I check the partition sizes with "df- h" in the terminal, incorrect sizes are reported. Partition 1 with actual size of 400GB is reported to be of 393GB only. Same goes for the other. It's showing lesser size. The same behaviour is observed in nautilus as well. The free space is shown less than the actual sizes of the partitions.

I also checked with Gparted. It's showing that 6.47GB of 400GB partition is already used.

How can I recover the used space? I already set the percent of reserved block to 0.

Thanks,

---

