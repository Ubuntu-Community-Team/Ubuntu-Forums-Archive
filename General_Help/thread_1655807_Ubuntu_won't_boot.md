---
title: "Ubuntu won't boot"
date: 2010-12-30
forum: General Help
---

### Post by Nicolice on 2010-12-30
Actually after installed the 2.6.36, my ubuntu working fine..but now seems I can't get it to boot now..
Got the stable kernel from 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

The situation is like this.

- Boot up the kernel 2.6.36
- Ubuntu logo comes out, and no activity
- Pressed ESC, and it shows
```
Setting up fstab
```

And will run up to hours without anything, no logs...

Reinstalled the kernel, won't work too :mad::mad:

---

### Post by davidmohammed on 2010-12-30
what version of ubuntu and why are you using the kernel from mainline rather than the kernel that came with ubuntu?

Graphics card?

Have you tried any boot options?

---

### Post by Nicolice on 2010-12-30
I was told the newer kernel have better performance, and kind of solved the performance issues in the older kernel so I just upgrade it to the latest maverick stable kernel.

But it won't boot, just stop at "setting up fstab"..

But when I revert to using 2.6.35-24 ..doesn't have such problem

---

### Post by davidmohammed on 2010-12-30
you've found your answer - stick with the .35 kernel.

What performance issues do you have with the .35 kernel that was supposed to be fixed in .36?

I noticed there are a couple of .37rc maverick kernels as well.  Do they resolve your issues?

---

