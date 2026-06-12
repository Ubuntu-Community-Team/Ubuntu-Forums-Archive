---
title: "Unallocated partition"
date: 2010-10-18
forum: General Help
---

### Post by spuny on 2010-10-18
After I formated my windows partition using GParted it became Unallocated and moved under Extended partitions. I can't create the unallocated partition as primary one, or drag it out of the extended ones. I tried GParted live CD also, but nothing worked. Can anyone help please?

---

### Post by VMC on 2010-10-18
> **spuny said:**
> After I formated my windows partition using GParted it became Unallocated and moved under Extended partitions. I can't create the unallocated partition as primary one, or drag it out of the extended ones. I tried GParted live CD also, but nothing worked. Can anyone help please?

Did you reboot after you? Also did you check gparted info that it gives for any information. If you expand, using the "+" symbol, it will reveal some pertinent information.

---

### Post by Megaptera on 2010-10-18
How many primary partitions are there already? I think the limit is three, then you have to have 'logical' partitions.

---

### Post by foxmulder881 on 2010-10-18
> **Megaptera said:**
> How many primary partitions are there already? I think the limit is three, then you have to have 'logical' partitions.

You can have up to 4 primary partitions per drive.

---

### Post by spuny on 2010-10-18
Yes I tried everything, and I have only one primary. Here's a Screenshot. I cannot move either swap or the unallocated.

---

### Post by foxmulder881 on 2010-10-18
If that were me, I'd be formatting and resinstalling the operating systems from scratch and clean up the whole drive. Any reason your swap ended up at the beginning of the drive also?

---

### Post by plucky on 2010-10-18
What partition setup do you require?

You cannot alter anything within the extended partition if any partition in the extended partition is mounted.Linux will usually mount the swap partition even on the Live CD.So you will have to un-mount everything in the extended partition and turn swap off.

Good Luck

---

### Post by Legeril on 2010-10-18
I had a problem with un-responsive partitons using Gparted, if they are mounted by in Ubuntu then they are unaccessible - they same goes for if they are mounted in Gparted then you can't access them in Ubuntu either. Try closing Gparted un-mounting everything then having another look

---

