---
title: "partitions ande cloning HDs, partition help."
date: 2010-03-30
forum: General Help
---

### Post by Humans_Are on 2010-03-30
I have a laptop that I just "returned to factory condition" and I'm planning on making a clone of the windows drive c partition after I revo and "decrapify" it. I looked for software to clone and ended up coming across linux and the DD commands, which is a method I'd feel most comfortable with. I read that the HD being copied to(receiving the clone) has to be bigger than the source HD. My laptop hd is about 475gb with two partitions, windows drive c, and the recovery partition drive d. Would it be possible to use Gpartition to make my windows drive c smaller, as small as it can go, and also create a new partition, drive e, for the clone? after the back up of the small windows C partition is cloned to the large new E partition could I then make the windows partition larger and the back up(drive E) smaller with gpartition? 
does anybody have tips for making HD backups? Could I make a small partition on my external and use that? Also how would I perform a recovery? say I had the back up on my external... would I just reverse the process, formatting my laptop and then using a live ubuntu cd and the DD command to copy my backup to the fresh HD? Would there be any issue with this or will I be ready to go right when the copy is complete?

edit, also this is windows 7 64bit home
Thanks, Matt

---

### Post by 2hot6ft2 on 2010-03-30
First you should use the windows disk management utility to shrink the windows partition instead of GParted.
Do a disk cleanup and defrag first before shrinking it.

Then look at clonezilla for doing the cloning part since many people recommend it.
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by Humans_Are on 2010-03-31
Thanks for the info. Now my issue is the partition shrinking... There are fragmented files stuck at the end of the partition in the C:system volume information folder...   and ideas on fixing this?

edit:  well, i fixed some of the issue... now i have MTF files or something like that in the middle of the partition...

i guess i'll just go with it and make a backup image of that 250 gig... @$#$!

---

### Post by chrisinspace on 2010-03-31
> **2hot6ft2 said:**
> Then look at clonezilla for doing the cloning part since many people recommend it.
[http://clonezilla.org/](http://clonezilla.org/)

+1 for Clonezilla.  It's great. It's not the most attractive UI, but it is free and effective.

---

