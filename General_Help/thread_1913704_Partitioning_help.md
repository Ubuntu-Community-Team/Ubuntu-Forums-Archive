---
title: "Partitioning help"
date: 2012-01-23
forum: General Help
---

### Post by Latham23 on 2012-01-23
sorry if this is in the wrong section, didn't know where else to post.  
 
I  have partitioned my hard drive for dual booting ubuntu 11.10 and  windows 7. However, I made a stupid mistake. Seeing as windows already  took up 3 primary partitions, I created an extension partition (which  took up the last of the 4 primary partitions available). Instead of  partitioning the rest of the hard drive, I partitioned all but 85ish GB,  so now I have 85GB sitting on my hard drive that isnt accessible as I  cannot move it to the extension partition or make it a new partition.  
 
So  what do I do with the free hard drive space now? I really can't be  bothered doing a whole new installation of windows as I will have to  restore windows after I delete the partition ubuntu sits on and recreate  windows 7 from the disk image etc etc. 
 
Help will be much appreciated, 
 
Latham

---

### Post by WthIteh on 2012-01-23
> **Latham23 said:**
> I  have partitioned my hard drive for dual booting ubuntu 11.10 and   windows 7. However, I made a stupid mistake. Seeing as windows already   took up 3 primary partitions, I created an extension partition (which   took up the last of the 4 primary partitions available). Instead of   partitioning the rest of the hard drive, I partitioned all but 85ish GB,   so now I have 85GB sitting on my hard drive that isnt accessible as I   cannot move it to the extension partition or make it a new partition.  
  
 So  what do I do with the free hard drive space now?
[LIST=1]
[*]Boot using live CD,
[*]Disable any swap partition which is in use (if any) by "swapoff -a",
[*]Open "gparted",
[*]Then "resize" your extended partition to fill the remaining free space (DO NOT change your logical partitions),
[*]Then you can create a new "logical" partition in the free space in the extended partition.
[/LIST]

---

### Post by carl4926 on 2012-01-23
You could resize the extended space
Then resize the logical partitions it contains to take up that space.

---

### Post by Latham23 on 2012-01-23
Sweet, cheers for the help guys.

---

