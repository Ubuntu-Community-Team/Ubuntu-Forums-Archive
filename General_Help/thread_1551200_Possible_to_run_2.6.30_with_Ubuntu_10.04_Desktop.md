---
title: "Possible to run 2.6.30 with Ubuntu 10.04 Desktop?"
date: 2010-08-12
forum: General Help
---

### Post by theshwam on 2010-08-12
Hello all,

I'm working on a project where I need to sanity check some things using hardware performance counters. I'm using the perfmon2 library which needs a patched kernel 2.6.30 (as far as I can tell this and earlier kernels are the only ones supported). 

I have built 2.6.30 with the patches and it works, but only in console mode. I guess something happened with udev between versions because the first error I get is "unable to mount none on /dev" and from there on X starts up fine but the mouse and keyboard don't work. According to this thread: [http://ubuntuforums.org/showthread.php?t=1435968](http://ubuntuforums.org/showthread.php?t=1435968) the problem lies in the old kernel. 

I can do alt+sysRq+r to grab the keyboard from X and then drop to a text console and do my work there (the performance counters work great), but nothing else works (X, wifi can't associate, etc). So I'm wondering is there any workaround so I can use my computer as normal with 2.6.30 on Ubuntu desktop 10.04 amd64? 

Alternatively, is there a performance counter library that works with 2.6.32 ?

Thanks

---

### Post by dino99 on 2010-08-12
im using 2.6.35 pae with no trouble, you can update your synaptic repo tab by changing "lucid" by "maverick", update then only install the new kernel (headers + image) then change back to "lucid" and update again to clean the repo, and that it.

---

### Post by inameiname on 2010-08-12
Or another option on installing the newest kernel, if you do feel like it, is to copy and paste this into the terminal:

sudo add-apt-repository ppa:kernel-ppa/ppa
sudo apt-get update
sudo aptitude install linux-headers-2.6.35-15-generic linux-image-2.6.35-15-generic

You can then use Synaptic every once in a while to see if there is a newer one out, as, sadly, they don't auto-update. 

Oh, and the 'pae' version is available as well.

---

### Post by theshwam on 2010-08-12
Sorry, I'm not sure how you guys got the impression that I wanted to run a newer kernel than what I currently have, but it's actually the opposite: I currently have 2.6.32 running fine, but I want to run 2.6.30 ...

---

### Post by dino99 on 2010-08-12
so make your choice  :p

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by sdennie on 2010-08-12
I'm pretty sure the reason that the patches only support up to 2.6.30 is because they were integrated into the mainline kernel in 2.6.31.  See: [http://anton.ozlabs.org/blog/2009/09/04/using-performance-counters-for-linux/](http://anton.ozlabs.org/blog/2009/09/04/using-performance-counters-for-linux/)

The 2.6.32 Ubuntu kernel has this turned on:

```

$ grep PERF_COUNT /boot/config-`uname -r`
CONFIG_PERF_COUNTERS=y

```

---

### Post by theshwam on 2010-08-12
EDIT: oh -- I see...   huh I wonder why when I run pfmon it doesn't detect the right sys/ directories that it looks for it with my 2.6.32 kernel ... 

Thanks for the heads up -- I will try to investigate further ...

EDIT2: I see -- pfmon is part of an old branch which uses a different set of kernel interfaces (pre 2.6.31) and libpfm4 uses a new set of interfaces that have been merged into latest kernels. Awesome, thanks!

---

