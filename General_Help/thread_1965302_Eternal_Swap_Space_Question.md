---
title: "Eternal Swap Space Question"
date: 2012-04-25
forum: General Help
---

### Post by oaxacamatt1 on 2012-04-25
Hi all,
I have been using Xubuntu 11.10 on a *very standard Toshiba L-305 notebook circa 2008*. When I set up my partitions, I used 5.39 Gb for my swap space.  Since I have 2 jiga's (a friends spanish pronounciation for gigabyte's) of RAM I thought that would be fine.

However, I have been watching my swap usage via conky and have noticed that I **NEVER** use it????  This perplexes me... 

How can I utilize swap more effectively (via **swapiness**) and will this increase my speed? I should say I do mostly surfing and document production but do on occasion use R, GIMP and audio and I thought those programs were generally memory hunger, i.e. swap hunger too.

Any comments, suggestions??

---

### Post by oldos2er on 2012-04-25
It's good you're not using any swap, because it would noticeably slow your system down. Hard disk access is magnitudes slower than RAM access. [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by jerome1232 on 2012-04-25
Firstly double check that your swap is actually activated (use free -m, check the swap line for a total), if it is, then celebrate, it is generally good you are not swapping.

---

### Post by kurt18947 on 2012-04-25
+1 to what oldos2er said.  I think on modern machines swap partitions are over rated.  I have one old machine with 512 MB. RAM.  I make sure there's swap available for it -- I went with about 600 MB.  For a machine with 2 GB, unless you're using RAM hungry programs or running one or more virtual machines, you probably won't ever use swap except to hibernate/suspend-to-disk. Hibernation does require a swap *partition*, a swap file won't work.   In the past I've created a swap *file* but haven't done so the past couple installs on a 2GB. machine and haven't had any problems.  In fact I set up an 11.10 install with a Win7 virtual machine.  With both OSs active I was still using just under 1 GB. RAM.

---

### Post by oaxacamatt1 on 2012-04-25
Thanks for the quick response OS2'er,
(I used that too for some really old scientific software in the earlier 90's)

Getting back to the Swap question...  Then why can't I get away with partitioning less swap space (e.g. 1xRAM) the next time a do a clean install with linux?

---

### Post by jerome1232 on 2012-04-25
Go for it, keep slightly more than total ram if you want to retain hibernate capability.

---

### Post by oaxacamatt1 on 2012-04-25
Hi Jerome,
**free -h** does not work on my systm but **free -m** gives me this:

[300][mcc.xdolly: /home/mcc]$ free -m
             total       used       free     shared    buffers     cached
Mem:          1883       1638        245          0        126        840
-/+ buffers/cache:        671       1212
Swap:            0          0          0

Which makes me think that there is NO swap utilized.

ALSO;

[302][mcc.xdolly: /home/mcc]$ swapon -a
swapon: cannot find the device for UUID=dd531c1e-c100-4ef9-aced-9abc88d7a522

---

### Post by jerome1232 on 2012-04-25
Your right, if you follow the link oldos2er provided, it details how to fix that.

---

### Post by oaxacamatt1 on 2012-04-25
I think I know what happened...  

I installed Debian on another partition and it renamed the swap file...
I believe all I have to do is go in and change the /etc/fstab to reflect that change.

Sorry all, but thanks for the leads!

---

