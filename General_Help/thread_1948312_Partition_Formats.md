---
title: "Partition Formats"
date: 2012-03-28
forum: General Help
---

### Post by Miykel on 2012-03-28
G'Day;  Does someone know the difference between  

[ Ext.2  and   Ext 4 Journaling ]

Partition Formats please.

Regards Miykel

---

### Post by Paqman on 2012-03-28
Do you want the exact nitty-gritty differences in the spec, or just the high-level overview?

Generally ext4 is just a more advanced version of ext2 and ext3. As you mentioned, it has journalling, which should help protect your data in the case of faults. Apart from that is really just a range of small tweaks and performance improvements.

Ext2 is obsolete, there's no reason to choose it over ext4

---

### Post by winh8r on 2012-03-28
> **Paqman said:**
> Do you want the exact nitty-gritty differences in the spec, or just the high-level overview?

Generally ext4 is just a more advanced version of ext2 and ext3. As you mentioned, it has journalling, which should help protect your data in the case of faults. Apart from that is really just a range of small tweaks and performance improvements.

Ext2 is obsolete, there's no reason to choose it over ext4

+1 for this concise explanation.



For a deeper explanation look here:

[http://en.wikipedia.org/wiki/Ext4]("http://en.wikipedia.org/wiki/Ext4")

---

### Post by dcstar on 2012-03-28
> **Paqman said:**
> 
.........
Ext2 is obsolete, there's no reason to choose it over ext4

Apart from using it on USB drives where you don't want to wreck them with too many write cycles, maybe.

Or using it on an SSD for something like Swap files where you want TRIM to actually work (unlike a Swap Partition) and using EXT4 is bone-headed, maybe.

Hang on, there's a couple of reasons already!

---

### Post by Paqman on 2012-03-28
> **dcstar said:**
> Apart from using it on USB drives where you don't want to wreck them with too many write cycles, maybe.


That's a possible reason, but of arguable validity. What's a greater risk to your data, using an unjournalled file system, or flash wear?

> 
Or using it on an SSD for something like Swap files where you want TRIM to actually work (unlike a Swap Partition) and using EXT4 is bone-headed, maybe.


Tbh, using swap at all on an SSD is not a great idea IMO. Get more RAM and wind swappiness down to zilch.

---

### Post by Miykel on 2012-03-28
Thanks so much for the replies guy's, that helps heaps, the answers I found on the net were so complex I ended up with brain ache  lol.
Kindest Regards Miykel

---

### Post by dcstar on 2012-03-28
> **Paqman said:**
> 
........
Tbh, using swap at all on an SSD is not a great idea IMO. Get more RAM and wind swappiness down to zilch.

People are increasingly using SSDs are direct replacements for rotational drives, and the current list of things that you ***"have"*** to do to make them work correctly is becoming a bit of a joke.

**Every** single partition used on a SSD has to support TRIM, otherwise the pool of empty blocks will be used and the SSDs write performance will go down the toilet.

Putting a Swap **partition** (AFAIK) on a SSD virtually guarantees eventual performance degradation once all the empty blocks are consumed and are never released back into the device. A Swap **file** on a TRIM supported partition (like EXT2) will not have this problem.

---

### Post by Paqman on 2012-03-28
> **dcstar said:**
> People are increasingly using SSDs are direct replacements for rotational drives, and the current list of things that you ***"have"*** to do to make them work correctly is becoming a bit of a joke.


I think a lot of folks talk a lot of rubbish about SSDs. On current drives with wear-leveling built in there's no need to do most of the write-reduction nonsense that some people recommend. All I do is push stuff into RAM, which isn't a specifically SSD-based optimisation. You can mess around with schedulers and the like if you really want but it's far from necessary. Ubuntu uses relatime by default, which is fine IMO.

The only thing that's really "essential" is adding discard to /etc/fstab.

> 
Putting a Swap **partition** (AFAIK) on a SSD virtually guarantees eventual performance degradation once all the empty blocks are consumed and are never released back into the device. A Swap **file** on a TRIM supported partition (like EXT2) will not have this problem.

If you're using a swap file anyway, why bother putting it on a separate partition at all?

---

