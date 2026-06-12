---
title: "get linux kernel version from distro on a different partition?"
date: 2010-06-09
forum: General Help
---

### Post by pythonscript on 2010-06-09
I'm currently using a triple boot system on my netbook between WinXP, lucid, and arch, and I'm trying to work out my grub entries (which I update *from lucid*). Here's what I have for my ubuntu menu entry, just the text: 

```
menuentry "Ubuntu Linux 10.04, $(uname -r)" {
```

How would I use a command like this to echo the kernel version of arch, which is installed on a different partition? This prints out in grub2, by the way:  

Ubuntu Linux 10.04, 2.6.32-22-generic

Is there a way to set the "root directory" of uname -r to a different partition with a flag? I couldn't find one in the man page but maybe I missed it.

---

