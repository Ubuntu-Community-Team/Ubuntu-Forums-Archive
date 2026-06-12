---
title: "Grub2 syntax"
date: 2010-07-27
forum: General Help
---

### Post by Intrepid Ibex on 2010-07-27
Just wanting to know whatfor are the commands "make active" (to 'activate' the partition. The grub2 wiki says it's now part of the parttool - how's that to be used?) and "insmod ntfs" needed with Windows 7.

I myself don't need either of those.

---

### Post by Intrepid Ibex on 2010-07-29
Does anybody know?

---

### Post by john newbuntu on 2010-07-30
As I understand it, The 'parttool /dev/sda1 boot' changes the boot flag to sda1 clearing the active flag on other partitions in an MBR style partitioning scheme.  There are I believe other options to parttool like "parttool /dev/sda1 hidden" that can be used to hide the sda1 partition.  This could be useful if you have multiple windows partition and want to hide one and use the other.

The insmod is for dynamically inserting modules to grub, in your example, the ntfs module so that it can help boot windows OS.

---

### Post by Intrepid Ibex on 2010-07-31
Yeah, well I guess the module's autoloaded as the Window's boot record is in the same partition.

So I take it it's only there so that the module will be force loaded despite how the fs was recognized as... but that will do no good since Windows will most likely be unable to boot in that kinda condition anyway without repairing the partition with the DVD.

---

