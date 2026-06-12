---
title: "Kernel file cache not released?"
date: 2011-01-04
forum: General Help
---

### Post by GeneralZod on 2011-01-04
Hi all, I have a rather odd problem with memory usage on my Kubuntu 10.10 install which is causing very unpleasant performance issues. 

Firstly, to get this out of the way: I know that Linux will cache files in memory in order to increase performance, and that sometimes it will do this even if it means pushing running processes into swap. However, the file cache is supposed to be releasable if applications need to use the memory instead. 

What's happening with my install is that a progressively larger and larger amount of RAM is taken up with cache, *and is never released*, even if I manually attempt to release the cache by cat'ing 3 into /proc/sys/vm/drop_caches as root*. The upshot of this is that memory available to processes shrinks and skrinks until it is so swappy that I have to log in and out again. Killing all memory hungry apps does little to alleviate the problem. 

So my question is: is it possible for a userspace app to use files in such a way that the contents cached by the kernel cannot be reclaimed and, if so, how do I go about finding the culprit? I'm vaguely sure that a userspace app is at fault as logging in and out of KDE seems to fix it for a while.

Here's the output of free -m as I was writing this, just after manually "dropping" the cache: 

```

             total       used       free     shared    buffers     cached
Mem:          2004       1826        177          0          0        **773**
-/+ buffers/cache:       1052        952
Swap:         1906        261       1644

```

I'm fairly certain that dropping the cache shouldn't leave me with almost 800MB still cached :)

Here's the output after logging in and out again and dropping caches:

```

             total       used       free     shared    buffers     cached
Mem:          2004        872       1132          0          0        **369**
-/+ buffers/cache:        502       1502
Swap:         1906          4       1901

```

I've set my vm.swappiness to 5 just in case the kernel was simply preferring to cache files at the expense of pushing stuff into swap, but this did not help.


* - Note that I'm not in the habit of doing this: I did it to find out why on Earth my laptop was swapping so horribly when there was allegedly so much memory "free" :)

---

### Post by matt_symes on 2011-01-04
Hi

Are you running sync with it

sudo bash -c "sync && echo 3 > /proc/sys/vm/drop_caches"

Kind regards

---

### Post by GeneralZod on 2011-01-04
Hi Matt,

Thanks for your response :) I am indeed sync'ing before dropping the caches :)

---

