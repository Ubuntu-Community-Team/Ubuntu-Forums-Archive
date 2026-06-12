---
title: "Resizing partition"
date: 2010-03-26
forum: General Help
---

### Post by s3a on 2010-03-26
I'm here: [http://tldp.org/HOWTO/LVM-HOWTO/reducelv.html](http://tldp.org/HOWTO/LVM-HOWTO/reducelv.html)

doing this part:
"# umount /home
# resize2fs /dev/myvg/homevol 524288
# lvreduce -L-1G /dev/myvg/homevol
# mount /home"

and I'm shrinking my home partition to make room for my root partition using LVM2 and my problem is a minor one but I don't know how to figure it out. I read the manual (man resize2fs) and it says that the -P parameter would give me the minimum size of a file system but how do I get the maximum size of a file system? Do I actually have to calculate it using basic arithmetic? I would like to avoid that because of the inaccuracies involved.

Any help would be GREATLY appreciated!
Thanks in advance!

---

### Post by srs5694 on 2010-03-26
The example commands you provide are for shrinking a logical volume and its filesystem. Are you attempting to increase the size of a logical volume and its filesystem? If so, you should resize the logical volume first and then use resize2fs without a size parameter; when called in this way, it will resize the filesystem to fill its container (partition or logical volume).

---

