---
title: "Extend Partition Problem"
date: 2011-06-05
forum: General Help
---

### Post by MadeOfEyelashes on 2011-06-05
I'm having some trouble extending my nfts partition. I didn't give myself enough space on my windows partition on accident and now I need more. I posted a picture of what my partition looks like. How can I extend my NFTS partition to hit the unallocated portion? [http://imgur.com/mQOy9](http://imgur.com/mQOy9)

[IMG]http://imgur.com/mQOy9[/IMG]

---

### Post by Mark Phelps on 2011-06-06
Well ... you've got a hard problem to fix ...

You can't (or really, should NOT) extend the first (100MB) partition because it is a "boot" partition and should only contain boot loader files.  

What you can TRY (presuming this is Win7), is to open the Win7 Disk Management utility and see if it will let you move the 100MB partition to the beginning of the unallocated space.

If that works, do the same again with the Win7 OS partition (move it to the left).

Once that is done, you can use Disk Management a third time to resize the Wint OS volume to take up some (or all) of the unallocated space.

Do NOT attempt to use GParted to do this -- doing so runs the risk of corrupting your Win7 setup and rendering it unbootable.

Also, BEFORE you try any of this, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need that later to repair the Win7 boot loader.

---

### Post by oldfred on 2011-06-06
I would normally suggest creating another NTFS partition just for data. But you have all your free space separated from the extended partition by two NTFS partitions. So you cannot create any more partitions nor expand extended to hold more partitions.

Moving partitions  is always more risky as all data has to be copied and verified, so be sure to have good backups.

---

