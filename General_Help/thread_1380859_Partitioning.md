---
title: "Partitioning"
date: 2010-01-14
forum: General Help
---

### Post by Overthere on 2010-01-14
Hi again everyone,
3 quick questions:
What program is good to install to partition my PC after installation (I installed without a partition). 
Also, any quick tips in partitioning?

Lastly,
I have an old Ubuntu installed together w/XP on another PC. I want to install Xubuntu to replace the old Ubuntu, using the same partition. Is that possible?

Thanks a billion!
Brian :KS

---

### Post by Grenage on 2010-01-14
> What program is good to install to partition my PC after installation (I installed without a partition).

You can't have installed without any partitions, but to configure partitions for free space you can use gparted:

```
gksu gparted
```

> I want to install Xubuntu to replace the old Ubuntu, using the same partition. Is that possible?

Yes, just format the partition and install using the disk.  There is probably an option to overwrite the partition; if not, just boot with the live CD and format the partition from the command line (or in gparted).

---

### Post by zvacet on 2010-01-14
Download [Gparted live Cd]("http://gparted.sourceforge.net/").It is very good tool.It is good idea to have separate home partition.I will put root as primary and home on extended(logical)partition.Swap also goes to the logical partition.To make separate home partition follow [this]("http://www.psychocats.net/ubuntu/separatehome") guide.

If your old ubuntu id version prior then Hardy (Ubuntu 8.04) you will have to install Xubuntu recent version on top of it.if you have Hardy or any version after that just follow [this]("http://www.psychocats.net/ubuntu/purexfce") to get Xubuntu-desktop.

---

