---
title: "Multiple Kernels at Boot"
date: 2010-01-24
forum: General Help
---

### Post by Ted3929 on 2010-01-24
A previous post discussed this matter but the resolutions posted, at least for me, didn't work.

I have at least 3 kernels in my grub menu ending with 2.6.31-17.  It's more an aggravation than anything else, but I'd like to get rid of all but one so my computer will boot quicker.

I tried Startup Manager but all that did was allow me to pick the main choice I desired (it deleted nothing) and Ubuntu Tweak doesn't give the option of deleted the older versions (either that or I missed it).

Any help greatly appreciated.

---

### Post by smerral on 2010-01-24
Well this is what I did:

sudo apt-get purge linux-image-2.6.31-14-generic

(or whichever kernel you want to remove)

---

