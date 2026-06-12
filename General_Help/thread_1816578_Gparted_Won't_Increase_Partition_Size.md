---
title: "Gparted Won't Increase Partition Size"
date: 2011-08-02
forum: General Help
---

### Post by moforilla on 2011-08-02
Hi,

I have booted up in a Gparted system disk.

I'm trying to use Gparted to resize my current linux partition. It sits on a one HDD with another Windows partition.

I have delete the windows partition (626GB) and now want to resize my linux partition to use all this unallocated space.

When trying to resize the linux partition (293GB) I am not able to do so. No space is shown to be available to use. I can only make the partition smaller.

Can anyone think of why I won't be able to increase my linux partition to use this now unallocated space?

[IMG]http://img837.imageshack.us/img837/2312/screenshotdevsdagparted.png[/IMG]

---

### Post by haresear on 2011-08-02
The Linux partition sda5 is a logical partition within the extended partition sda3. You must first resize the extended partition sda3 to include the unallocated space.

---

### Post by westie457 on 2011-08-02
> **haresear said:**
> The Linux partition sda5 is a logical partition within the extended partition sda3. You must first resize the extended partition sda3 to include the unallocated space.

+1
Also there must be no partitions mounted otherwise nothing will work.

This sort of repartitioning must be done with a LiveCD as you are already using one not a problem.

Some bits of advice. Do this one step at a time. That is extend the sda3 partition as far as it will go and click apply before making adjustments to the others. This to stop Gparted getting confused about which bit it should be doing and when. Have tried moving and extending some partitions and shrinking others in the past as one operation. That killed the hard drive partitioning and had to start again with clean installs and updates for Windows and Maverick. Stressing this point again do this one step at a time. It will be quicker in the long run.

---

### Post by dcstar on 2011-08-03
> **moforilla said:**
> Hi,

I have booted up in a Gparted system disk.

I'm trying to use Gparted to resize my current linux partition. It sits on a one HDD with another Windows partition.

I have delete the windows partition (626GB) and now want to resize my linux partition to use all this unallocated space.
.........

A far better strategy would be to create a new /home partition and move all the existing /home data to it.

Do a forum search for detailed instructions.

---

### Post by moforilla on 2011-08-03
Thanks for the help, I ended up using gparted and it worked fine.

---

