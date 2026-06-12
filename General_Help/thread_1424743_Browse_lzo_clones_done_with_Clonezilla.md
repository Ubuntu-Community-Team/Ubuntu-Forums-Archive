---
title: "Browse lzo clones done with Clonezilla"
date: 2010-03-08
forum: General Help
---

### Post by dragos2 on 2010-03-08
I made a full disk backup using Clonezilla on a external drive and I used lzo, but this time I need to browse its contents somehow and extract some files but I could not find a utility that reads lzo archives.

Do you know a way to browse these lzo clones ? Or a utility program that can help me: I already tryed 7zip, Winrar and peazip.

Thank you

---

### Post by howefield on 2010-03-08
From the clonezilla website...

> Limitations

The destination partition must be equal or larger than the source one.
Differential/incremental backup is not implemented yet.
Online imaging/cloning is not implemented yet. The partition to be imaged or cloned has to be unmounted.
Software RAID/fake RAID is not supported by default. It's can be done manually only.
Due to the image format limitation, the image can not be explored or mounted. You can _NOT_ recovery single file from the image. However, you still have workaround to make it, read this.

Go to clonezilla.org for the links to the workaround.

---

### Post by dragos2 on 2010-03-08
> **howefield said:**
> From the clonezilla website...



Go to clonezilla.org for the links to the workaround.

Thanks for pointing that out. Neither of the solutions are good since it involves creating
a virtual machine with a partition as large as the disk cloned.

So it seems that I can't just browse ..

---

