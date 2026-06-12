---
title: "gparted:&quot;Can't create more partitions&quot;"
date: 2010-06-30
forum: General Help
---

### Post by NeverHide on 2010-06-30
I've attached 2 Screenshoots from gparted.
I have 50GB unallocated free space in my disk and i want to make a new partition,but when i try to do it i get an error message saying i can't create any more partitions in this disk.
I don't know if this provides any usefull info but when i creating the linux partition,from the ubuntu disk, i selected the option "Primary" instead of "Logical"(or whatever it says) at the partition type 



P.S. something of the topic,how can i add images  within my text at my posts,not to attach them

Any ideas are welcome :D

---

### Post by garvinrick4 on 2010-06-30
Looks like you have 4 primarys going on and that is all you get.
Can you increase the size of your extended so you can use that space.
And yes the linux should have been inside of the extended in a logical, would have saved a 
primary. I do not know how much Ram you have if 2 gig or more would not worry
about the swap. But you will be able to use your unused space.
 Right click and choose resize on your extended. And see if you can delete swap.
If have under 2 gig of Ram keep it.

---

