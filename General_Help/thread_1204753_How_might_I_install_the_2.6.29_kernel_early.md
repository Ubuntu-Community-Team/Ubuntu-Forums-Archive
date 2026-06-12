---
title: "How might I install the 2.6.29 kernel early?"
date: 2009-07-05
forum: General Help
---

### Post by diablo75 on 2009-07-05
In [this thread]("http://ubuntuforums.org/showthread.php?t=1181733") others have reported a stability issue with certain atheros wireless chipsets being resolved by using kernel 2.6.29.  But the most recent updates I've gotten has me running a lesser version so I was wanting to try and install this newer one and see if it might solve this hardware lockup issue I'm having.  How might I do install this newer kernel that hasn't been officially "inducted" into the updates yet?

---

### Post by rob1408 on 2009-07-05
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/)

Install in following order:

1)linux-headers-2.6.29-020629_2.6.29-020629_all.deb

2)Your architecture headers, either amd64 or i386.

3)The image deb for your architecture

4)reboot

---

### Post by DeMus on 2009-07-05
> **rob1408 said:**
> [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/)

Install in following order:

1)linux-headers-2.6.29-020629_2.6.29-020629_all.deb

2)Your architecture headers, either amd64 or i386.

3)The image deb for your architecture

4)reboot

You can also go straight to 2.6.30. I did that a few weeks ago and I love it.
You can find it here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/")
Install in the same order as written above. This is mandatory.

---

### Post by diablo75 on 2009-07-05
Thanks everybody!  Can't wait to get home and un-brick my frozen PC to apply this kernel.

---

