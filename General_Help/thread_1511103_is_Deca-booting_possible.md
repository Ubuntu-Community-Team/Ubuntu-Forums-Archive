---
title: "is Deca-booting possible?"
date: 2010-06-16
forum: General Help
---

### Post by ubunterooster on 2010-06-16
Or will it fry poor grub? I have Mint on my SSD and plan to stick all others on a 2 TB drive as the minute VM resolution is very distracting.


(in case you wondered the current plan for the 2TB drive is: Ubuntu 10.04, Ubuntu10.10, Mandriva, PCLOS, Fedora, Slitaz, Igelle, Arch, Gentoo, and may later grow)

---

### Post by dino99 on 2010-06-16
Deca ? dont know that, could you give some lights ?

---

### Post by ubunterooster on 2010-06-16
deca=10

"Give some lights?"?

---

### Post by warfacegod on 2010-06-16
Do it! If for no other reason than to report your success or abysmal failure.

This might be useful: [http://ubuntuforums.org/showthread.php?t=1462617]("http://ubuntuforums.org/showthread.php?t=1462617")

And after you totally fragged GRUB, section 13 might be useful: [http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by warfacegod on 2010-06-16
Another suggestion: Don't even *bother* trying to keep your files on the machine until your sure it's stable.

---

### Post by dino99 on 2010-06-16
> **ubunterooster said:**
> deca=10

"Give some lights?"?

the limits are your disks free space :lolflag:

---

### Post by eriktheblu on 2010-06-16
At one time I had 4, but lost interest in the others. 

I've seen a report about a guy who had at least 10, but I think it was more like 20-50 on a single boot loader. Can't find it now.

---

### Post by ubunterooster on 2010-06-16
I will later post how things are going; will mark as "solved" for now and remark as "unsolved" if things go south


> **warfacegod said:**
> Do it! If for no other reason than to report your success or abysmal failure.

This might be useful: [http://ubuntuforums.org/showthread.php?t=1462617](http://ubuntuforums.org/showthread.php?t=1462617)

And after you totally fragged GRUB, section 13 might be useful: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)Thanks for the link.

> **warfacegod said:**
> Another suggestion: Don't even *bother* trying to keep your files on the machine until your sure it's stable.
I can quickly get things back to how they were with my backups
> **dino99 said:**
> the limits are your disks free space :lolflag:
2TB @ 20GB per OS and 20GB SWAP; I can install 99 theoretically?
> **eriktheblu said:**
> At one time I had 4, but lost interest in the others. 

I've seen a report about a guy who had at least 10, but I think it was more like 20-50 on a single boot loader. Can't find it now.
I had 4 at one point also

---

### Post by ubunterooster on 2010-06-18
I removed the SSD and installed all other OSs, put SSD back in, booted, ran Update grub.
And, I have lots of choices. :D

Edits: >   [COLOR=blue]**In Linux a Pata (or IDE) disk can have 63  partitions maximum and the limit of a Sata or SCSI disk is 15**[COLOR=Black]Explains why I could not make 100 partitions
[/COLOR][/COLOR]

---

### Post by oldfred on 2010-06-19
this is older and on another forum. He uses old grub that lets you install grub to the install partition to allow chainbooting. Otherwise menu maintenance is a nightmare. Grub2 does not like to be installed to a partition.

chainboot 145 systems (two drives)
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)

---

