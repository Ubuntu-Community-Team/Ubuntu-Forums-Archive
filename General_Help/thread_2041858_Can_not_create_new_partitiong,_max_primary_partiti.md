---
title: "Can not create new partitiong, max primary partitions used?"
date: 2012-08-13
forum: General Help
---

### Post by uschxc on 2012-08-13
I have an LVM on a server that we've been creating new partitions off of the main disk (which is really a datastore in VMware vSphere) and have apparently run into a problem where there are too many primary partitions defined, and we can not create an extended logical volume

[See attached image]

Unfortunately the LVM's volume is nearing capacity, so I need to figure out something very soon.   I know how to add a partition as a physical volume to a volume group and expand the LVM, but how do I get the free space into a useable partition from here?

---

### Post by dcstar on 2012-08-14
> **uschxc said:**
> I have an LVM on a server that we've been creating new partitions off of the main disk (which is really a datastore in VMware vSphere) and have apparently run into a problem where there are too many primary partitions defined, and we can not create an extended logical volume


Make a new disk in VMware and use that. If you have used the maximum of 4 Primary Partitions on the existing disk then delete a Primary Partition and recreate it as part of a new Extended Partition.

---

