---
title: "Partioning Help"
date: 2009-07-11
forum: General Help
---

### Post by celtic426 on 2009-07-11
Hi,  I need some help resizing some paritions.  I want to resize C to make it bigger.

[IMG]http://img17.imageshack.us/img17/145/parition.jpg[/IMG]

As you can see, I have a C partition, then an extended partition with a storage drive, two linux drives, and a swap drive.  

I dont mind losing one of the linux drives, but Im kinda stuck on what to do because the last four partitions are all inside one extended partition.

Any help is appreciated!!

---

### Post by merlinus on 2009-07-12
You will first have to delete and/or shrink one or more of the logical partitions, then shrink the extended partition, and finally grow c: into the freed-up space.

Is this a wubi install?  If not, then gparted may be the tool of choice.

---

### Post by ralphmcknight on 2009-07-12
you may need to "drop" the links to all of the partitions first.  drop is on the gparted manu.

---

### Post by celtic426 on 2009-07-12
Thanks, I just shrunk the linux partitions and moved them around and that worked.  Thanks for the help.

---

