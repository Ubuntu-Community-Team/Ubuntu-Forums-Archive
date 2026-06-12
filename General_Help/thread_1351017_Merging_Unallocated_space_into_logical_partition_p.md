---
title: "Merging Unallocated space into logical partition problem"
date: 2009-12-09
forum: General Help
---

### Post by stark222000 on 2009-12-09
I recently installed ubuntu on a partition and i finally got it all set up after a lot of trouble with wireless drivers. now i have decided to get rid of windows so i deleted that partition and though i could just expand the ubuntu partition but it doesn't work. i read up on it and even booted from a live cd and it won't let me expand. i can't reinstall in on the whole hard drive because the only way for me to set up the wireless driver was to go onto windows first and since i deleted that i can't go through that again (don't ask why i had to go onto windows to set it up, long story). so is there anyway to just add the unallocated space to the logical drive or what?

---

### Post by ajgreeny on 2009-12-10
The logical drive will be enclosed in an extended partition, probably along with the swap partition.  You will need to enlarge the extended partition first, so have a good look in gparted on the live CD as you cant use an installed version of gparted to do anything to mounted partitions, which they will be on an installed version.

Both your partitions will appear in an enclosing partition numbered between sda1 and sda4, exactly which number will depend on your original partition table.  Enlarge that first and then enlarge the ubuntu partition(s) and all should be well.

If this does not make sense, show a screenshot of gparted, and I will be able to talk you through it again.

---

### Post by stark222000 on 2009-12-19
> **ajgreeny said:**
> The logical drive will be enclosed in an extended partition, probably along with the swap partition.  You will need to enlarge the extended partition first, so have a good look in gparted on the live CD as you cant use an installed version of gparted to do anything to mounted partitions, which they will be on an installed version.

Both your partitions will appear in an enclosing partition numbered between sda1 and sda4, exactly which number will depend on your original partition table.  Enlarge that first and then enlarge the ubuntu partition(s) and all should be well.

If this does not make sense, show a screenshot of gparted, and I will be able to talk you through it again.


thank you very much that worked. i'm kind of ashamed of myself for not knowing that because i've worked with patitions a lot before, just not logical ones it would seem or ubuntu at all. that was very helpful and worked perfectly.

---

