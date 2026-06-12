---
title: "Question about cloning a Windows partition"
date: 2012-06-18
forum: General Help
---

### Post by O2Blevel on 2012-06-18
I know how to clone a partition but the question I have is can I compress the clone and still be able to reverse the process and recreate my windows partition exactly if something goes wrong. I have limited space on my backup computer so I want to bzip the clone and to speed things up a bit I'm considering zeroing the unused space on the partition. I think it should be ok, but I just want to check what others have to say and if there is anything special I should do beforehand. I'll be using dd to clone the partition.

---

### Post by sudodus on 2012-06-18
You can use ***Clonezilla*** from a boot CD or USB drive and make an image, with compressed file data. Unallocated space is skipped.

This way you can make an image of the whole drive or of one or more partitions. It is a good way to make a complete backup. I use it and I have restored successfully from the images.

If you want to be sure, get one external drive and on extra internal drive, make your image on the external drive and restore it to your new internal drive. Then insert it to test that it really works!

---

### Post by O2Blevel on 2012-06-18
Thanks for the quick reply, I didn't know Clonezilla skipped unallocated space, I guess that's partly why it's so fast. I haven't used it before but will give it a try.

---

### Post by Mark Phelps on 2012-06-18
Clonezilla skips unused space -- that is space inside a partition.  Unallocated space is space OUTSIDE of any partition.

Also, since Clonezilla does that, it's not an "exact" copy of your partition because the unused space isn't copied.

Plus, you can also download, install, and use the FREE version of Macrium  Reflect, from inside MS Windows, to accomplish the same thing.

---

