---
title: "renaming/rearranging OS in Grub 2?"
date: 2009-12-15
forum: General Help
---

### Post by chellrose on 2009-12-15
(Disclaimer: This probably isn't *technically* an Ubuntu question, but for some reason the darn thing _insisted_ that I give it a thread prefix...)

I have a laptop that came with Windows 7.  Naturally, the first thing I did was to add Ubuntu and make it dual-boot :).

For some unknown reason, Windows had 3 partitions on the hard drive.  Being relatively new at this, I resized the largest one (which contains the actual OS) to make room for Ubuntu, leaving the other 2 alone.

Now GRUB lists two of the Windows partitions with the same name: Windows 7 (loader).  It does give the partition number for each, so I am able to distinguish them... but I'd prefer them to have distinct names.  Thus:

1) Can I change the name in GRUB without messing something up (or does it _need_ to call it by that name in order to work), and

2) Can I change the order of partitions in GRUB, so as to make the "main" Windows partition appear before the two others (but still leaving Ubuntu as the first, and default)?

Thanks!

---

### Post by chellrose on 2010-03-09
Anyone? :)

---

### Post by dcstar on 2010-03-09
> **Sissy13 said:**
> Anyone? :)

I believe that the various Grub2 HOWTOs cover these things, search them out.

---

### Post by Bradj47 on 2010-03-09
Try looking at the **/boot/grub/menu.lst** file. Then you can edit the entries in the GRUB boot menu.

---

### Post by darolu on 2010-03-09
> **Bradj47 said:**
> Try looking at the **/boot/grub/menu.lst** file. Then you can edit the entries in the GRUB boot menu.

This will only work with GRUB Legacy, considering he made a fresh install and his mini-profile say he uses Karmic; seems like this won't work for Sissy13.

This link provides info that may help to do what you want: [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

