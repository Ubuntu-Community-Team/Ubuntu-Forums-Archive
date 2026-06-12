---
title: "Ubuntu  no longer boots!!"
date: 2010-07-09
forum: General Help
---

### Post by Mark Phelps on 2010-07-09
How ironic ... that just after my recent post about minor GRUB2 problems, I reboot my machine ... and now, Ubuntu won't boot at all!

I get the following text messages at the top of a black screen:
```
fsck from util-linux-ng 2.17.12
Lucid: clean
init: ureadahead-other main process (869) terminated with status 4
```

I Googled this error and all I found was bug reports from months ago, and I have NOT updated the 10.04 kernel in over a week!  So, why would this boot OK repeatedly today (have been doing that testing changes to the GRUB2 setup) and now, suddenly, refuse to boot anymore?

Also, holding down either Shift key, unlike before, does NOT display a GRUB menu anymore.

And, I booted into a 10.04 LiveCD ran fsck against the Lucid partition, and got the same results as above --> clean.

Update: Well .. since no-one is bothering to respond ... went ahead and fixed this myself.

---

