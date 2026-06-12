---
title: "mount issue  9.10"
date: 2009-11-06
forum: General Help
---

### Post by yilin on 2009-11-06
I don't know why but after upgraded from 9.04 to 9.10, during the booting it says one or more drive cannot mount and prompt for a manual fix(which i don't know how)

after some sort of timeout, i can login and all the linux partitions are mounted just fine but all ntfs partitions are not mounted (from Places, chose one of ntfs partition, it'll ask for password)

My concern is not about auto mount, I can live with manual mount for ntfs partitions, but the system take this as errors and I've experience twice that I cannot boot into ubuntu.

Anyone experienced the same issue? Anyone can help me get rid of such errors? 

Thanks

---

### Post by khelben1979 on 2009-11-06
Are you using [EXT3]("http://en.wikipedia.org/wiki/Ext3") or [EXT4]("http://en.wikipedia.org/wiki/Ext4") on the partitions?

---

### Post by yilin on 2009-11-09
Thanks khelben1979. 

Here are the partition info

Windows partitions: NTFs
Ubuntu partitions: EXT3
There are fat16 system partition and a Swap partition. See below:

[IMG]http://elinkage.net/images/partitions.png[/IMG]

---

