---
title: "No kernel modesetting driver detected"
date: 2009-10-09
forum: General Help
---

### Post by Quaxo76 on 2009-10-09
Hi all,
I have a laptop with an Intel video card. Suddenly my Ubuntu (9.04, just updated) stopped booting properly, giving the warning that it's running in low graphics mode. It says "No kernel modesetting driver detected" and "Screen(s) found but none have a usable configuration".
I noticed that I have, in /var/log, two logs: Xorg.0.log ad Xorg.1.log. The one with "0" is the only one that shows this error.
Any idea what happened, and how to fix it?

Thank you in advance,
Cristian

---

### Post by ff1111 on 2009-10-09
If you are using the xorg-edgers PPA or another cutting-edge xorg repository, you may be affected by this bug in xserver-xorg-video-intel:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/447181]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/447181")

I have this problem as well. 

I reverted to an older version of xserver-xorg-video-intel for now, until it is fixed.

---

### Post by Praxicoide on 2009-10-10
Thank you, I also had this problem, and that bug report took me to this wiki:

[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

Which is how I solved it, following the Jaunty portion (since I have a built 2.6.31 kernel).

---

### Post by anjo_ed on 2009-10-11
Thank you, i also had this problem and i solved with suggestion. :)

My system:
Notebook CCE OneBlack
Intel Chipset GM965 ( X3100 )

---

### Post by FirstByté on 2009-10-11
Hey,

A huge thanks for this post. I've been able to fix my GDM to normal now. 

However, the **modprode** seems to have gotten my **wlan** screwed up. I'll look for work arounds and post how I fixed this thing.

---

### Post by Quaxo76 on 2009-10-14
That driver was where the problem was, indeed... but instead of down-grading the driver, I upgraded to a new kernel, and that works, too! :) Thanks everyone!

Cristian

---

### Post by sinbin on 2009-10-16
> **Quaxo76 said:**
> That driver was where the problem was, indeed... but instead of down-grading the driver, I upgraded to a new kernel, and that works, too! :) Thanks everyone!

Cristian

Cristian can you explain please how you upgraded to a new kernel please. I have not done this before

Thanks
John

---

### Post by Quaxo76 on 2009-10-30
Hi John,
I simply followed an online guide (it was the first time for me, too). I can't find the exact guide I followed but it was extremely easy. I found this one:
[http://ubuntu.igameilive.com/2009/08/2630-kernel-on-jaunty-jackalope.html](http://ubuntu.igameilive.com/2009/08/2630-kernel-on-jaunty-jackalope.html)
What I did was done using the terminal, but I think the actual operations were more or less the same...

Cristian

---

### Post by Quaxo76 on 2009-10-30
[Edit: Removed double post]

---

### Post by Sylslay on 2010-06-09
I add to grub2 command line in Lucid, ctrl+e and
(unable to boot with same error, after use ppa drivers):

i915.modeset=1 gfxpayload=1024x768

and Ubuntu boot again,

---

### Post by lubo777 on 2010-06-15
> **Praxicoide said:**
> Thank you, I also had this problem, and that bug report took me to this wiki:

[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

Which is how I solved it, following the Jaunty portion (since I have a built 2.6.31 kernel).

yes, this link helped me solving the same problem also, but I had to recompile my kernel, because the i195 driver was compiled as a build in kernel module.

I activated CONFIG_DRM_I915_KMS=y and after the restart everything was OK.

---

