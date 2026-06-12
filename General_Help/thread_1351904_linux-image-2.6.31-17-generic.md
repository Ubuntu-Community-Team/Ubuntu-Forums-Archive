---
title: "linux-image-2.6.31-17-generic"
date: 2009-12-11
forum: General Help
---

### Post by ilna on 2009-12-11
linux-image-2.6.31-17-generic is released, but linux-image-generic still depends on older version. Does it mean I must just wait for linux-image-generic be updated to depend on 2.6.31-17, or must I install this kernel directly?

And, more common, is there information about kernel-in-ubuntu lifecycle, update policy, rules, traditions, advises and so on?

---

### Post by Silent Warrior on 2009-12-11
I was hit rather hard by going from 2.6.31-14 to -15 - took down my wireless, and with no wired connection available to me at the time... Took me three system reinstalls to figure this out. (So I'm not some bloody über-n3rd, mkay?) On the other hand, that is the only time I've ever had a problem with kernel updates.
Still, I believe the rule-of-thumb is to not update the kernel unless it comes with a fix you actually need.
I don't think there's any software that depends on your kernel, though kernel-modules are compiled against its corresponding headers - mismatched versions -> FAIL.

If you do go ahead, make sure to leave yourself a way of going back to the old kernel, just in case. And I want to make sure you get the hint that I don't think people should use the proposed-updates repository unless they receive clear instructions to do so.

---

### Post by ilna on 2009-12-11
Is it a "clear instructions"? :-)

[http://www.ubuntu.com/usn/USN-869-1](http://www.ubuntu.com/usn/USN-869-1)

---

