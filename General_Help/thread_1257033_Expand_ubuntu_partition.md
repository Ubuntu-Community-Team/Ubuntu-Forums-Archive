---
title: "Expand ubuntu partition"
date: 2009-09-03
forum: General Help
---

### Post by sharath0007 on 2009-09-03
Hi there,
i've installed ubuntu 9.04 in my lap recently. I have windows 7 also installed on the same system. At the time of installing, i had set 8gb of hard disk as the size of my ubuntu partition. However this space is now nearly full.
Can i increase the size of the ubuntu partition without having to reinstall the os? I dont care if this affects my windows partition.
Pl help!!!:p

---

### Post by Bucky Ball on 2009-09-03
You need to do this using the Live CD as the partitions need to be unmounted to resize.

Once booted into the Live desktop, System->Administration->Partition Editor. Resize (shrink) windows partition then expand Ubuntu partition into the free space that should be left.

Recommended you defrag the Windows partition before attempting this maneuver.

And of course back up valuables just in case things go pear shaped!

---

### Post by vedek on 2009-09-03
try gparted u should have it installed but if not check synaptic, you can then drag the size of your partition to make it bigger

---

### Post by Bucky Ball on 2009-09-03
> **vedek said:**
> try gparted u should have it installed but if not check synaptic, you can then drag the size of your partition to make it bigger

As above, you can NOT do this from an install because the Ubuntu partition needs to be UNMOUNTED to resize. Even when working on another data partition from within an installed Ubuntu you MUST unmount the partition to resize it. You MUST use a Live CD (Ubuntu Live or Gparted Live CD) to resize the Ubuntu partition itself.

:)

---

### Post by vedek on 2009-09-03
so thats why it didn't work with me i should have figured that it might be a problem, apologies for the incorrect advice.

---

### Post by Bucky Ball on 2009-09-03
> **vedek said:**
> so thats why it didn't work with me i should have figured that it might be a problem, apologies for the incorrect advice.

;-) Not to worry; it is a very common error. Confused myself for awhile working out that one which is how I know! lol

---

### Post by sharath0007 on 2009-09-03
Thank u guys for the kwik reply!!
I shall try this right away:d

---

