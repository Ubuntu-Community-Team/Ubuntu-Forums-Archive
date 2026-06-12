---
title: "Ubuntu Partion Problems"
date: 2009-07-18
forum: General Help
---

### Post by gilanib on 2009-07-18
[SIZE=1][SIZE=2]Salam,

My name is Mubashir Gilani. I am new in Ubuntu 9.04 OS.

I read the documentation and read that Ubuntu use "ext3" file system. If I install Ubuntu in my PC in C drive "which is NTFS formated drive". Did my other partitions are hide or remove when I install Ubuntu??

What should I do??

Please help.


Best Regards!!

Thanks!!

Edit bodhi.zazen - I edited this post and removed the bold and large font. Some people do not like such large fonts =)

Unless you have some reason, go with the defaults, and if you have a hard time reading adjust your browser 8)[/SIZE]         
[/SIZE]

---

### Post by Skatertjah on 2009-07-18
Since your new to Ubuntu I'd recommend installing using wubi instead of messing with your partitions too much. Wubi installs inside your Windows partition so you have no need to repartition. Besides that Wubi is very easy too learn. If you're really interested in installing Ubuntu on a seperate partition I'd recommend for you to become familiar with Linux before you try anything you don't yet understand. Partitioning can be quite harmful when you don't know what your doing...

Have fun learning;)

---

### Post by gilanib on 2009-07-19
Ok thanks.
 
But I backup my all data from D drive. D Drive is ow empty and has 10GB of free space. Can I install Ubuntu in D partition.?? Windows XP is already installed in C Drive. Can I format D drive with ext3 for Ubuntu OS.??
 
please help!!

---

### Post by 3rdalbum on 2009-07-19
Yes, you can install Ubuntu to your 10GB hard disk. Ten gigabytes is not very big for Ubuntu but it will run. Just follow the prompts in the installer and choose the 10 gigabyte hard disk as the target.

Note that Linux doesn't use drive letters, so the installer won't say "D drive" or anything like that. It will refer to device file names like "/dev/hda" or "/dev/sdb", and the size of the disk. The installer will format your 10 gigabyte disk for you, there's no need to do this before installing.

---

