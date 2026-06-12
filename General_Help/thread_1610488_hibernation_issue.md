---
title: "hibernation issue"
date: 2010-10-31
forum: General Help
---

### Post by glennharm on 2010-10-31
I have ubuntu 10.10 installed to a dedicated partition and hibernate and standby were working fine yesterday. 

Searching for similar issues, I've confirmed that my swap file is defined and mounted properly:

```
root@hw8:~# cat /proc/swaps 
Filename                                Type            Size    Used    Priority
/dev/sda4                               partition       6291452 0       -1
root@hw8:~# free -m
             total       used       free     shared    buffers     cached
Mem:          3963       1307       2655          0        121        487
-/+ buffers/cache:        698       3264
Swap:         6143          0       6143

```

If I start up gparted, and click on the swap partition, it gives me the "swapoff" context menu entry, so that would also indicate that the swap is enabled. 

I have 4G memory, so 6G should be sufficient (since it was working yesterday). 

I also saw some information about enabling hibernate in the gconf-editor, but that yields a (seemingly common) error and wont let me do that: 

```
root@hw8:~# gconf-editor
No protocol specified

** (gconf-editor:15268): CRITICAL **: Failed to parse arguments: Cannot open display: 

```

...of course the obvious question is "what changed since yesterday?". I was definitely messing with a number of things trying to get my hard drive running cooler, but I'd be hard put to enumerate the things I've done in that regard. 

Any help will be appreciated!

Thanks!

---

