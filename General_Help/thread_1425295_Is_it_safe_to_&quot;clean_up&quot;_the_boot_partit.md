---
title: "Is it safe to &quot;clean up&quot; the /boot partition?"
date: 2010-03-08
forum: General Help
---

### Post by TheAlien on 2010-03-08
After the recently 2.6.31-20 kernel update, my 100MB /boot partition is starting to lack space. When I examine it, I have a lot of old kernel files all the way back to 2.6.31-14.

Is it safe to just delete all the kernel files except for the 2.6.31-20 ones?

The only files and folders on that partition is just the grub folder and all the kernel files anyway.

---

### Post by oldos2er on 2010-03-08
It's best to use the package manager to uninstall kernels, that way grub shouldn't become confused. In Synaptic, search for linux-image and remove the appropriate version(s).

---

### Post by spillin_dylan on 2010-03-08
Yes, but I think everyone here will **strongly** recommend you remove the kernel headers and kernel images via Synaptic, or other similar means.

---

### Post by TheAlien on 2010-03-12
Thanks, it worked!

I uninstalled these three packages as a test:

linux-headers-2.6.31-14
linux-headers-2.6.31-14-generic
linux-image-2.6.31-14-generic

And now my boot partition got about 20mb bigger.

But why does Ubuntu store these old kernels?

---

### Post by Rocket2DMn on 2010-03-12
Old kernels are kept around to be used as alternatives to newer ones.  Sometimes users have issues with new kernels, or if something breaks in them, you can revert to an older one to either use permanently or use for recovery means.  Historically this has been an issue with driver compatibility, but these days it's not much of an issue. You usually don't need more than a few around for safety (chances are you will never need them though, but better safe than sorry).

---

### Post by Mark Phelps on 2010-03-13
FYI ... if you're running GRUB2 (as you would with a new install of 9.10) another PLUS of using Synaptic to remove the old kernel versions is that it automatically launches update-grub and generates a new GRUB2 menu -- devoid of the kernel versions you removed.

So, you no longer have to maintain your GRUB menu by hand-editing it.

---

