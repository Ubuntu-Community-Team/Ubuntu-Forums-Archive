---
title: "Upgrading to a new kernel"
date: 2012-08-19
forum: General Help
---

### Post by imnotanerd on 2012-08-19
I want to update my kernel to stop the occasional system freeze that happens. My internet search shows that the freezing is due to the HD 4000 graphics on my i7, and upgrading the kernel should do the trick. Now, [on here]("http://partiallysanedeveloper.blogspot.co.uk/2012/05/ivy-bridge-hd4000-linux-freeze.html"), they go with v3.3.6 of the kernel, but according to the [mainline kernel page]("http://kernel.ubuntu.com/~kernel-ppa/mainline/"), v3.4 is the latest kernel meant for 12.04. Should I go with v3.3.6 or go with v3.4?

---

### Post by Bucky Ball on 2012-08-19
These are not standard kernels for 12.04. That is at 3.2. You could try these 'bleeding edge' kernels, by all means, and although they may fix your issue they could create others. 

As for which you go for, the choice is yours, but I'm suspecting 3.4 could be reasonably unstable and expect changes. Of course, there is absolutely no guarantee they will fix anything if the problem is not kernel specific. There are updated drivers for your hardware in the more recent kernel?

---

### Post by imnotanerd on 2012-08-19
I'll go ahead and install 3.3.6 since that's what people followed and said everything still works, with the freezing gone. Thanks for your input!

---

### Post by Bucky Ball on 2012-08-19
Good luck. Think that is the beginning of the 12.10 kernels. Regard as testing. Wouldn't advise this for a production machine. ;)

---

