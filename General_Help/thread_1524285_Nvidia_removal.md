---
title: "Nvidia removal"
date: 2010-07-05
forum: General Help
---

### Post by MrGreen on 2010-07-05
Hi,

I loaded hardware drivers [nvidia] but they did not work, had a job to remove and get x working again. But still getting error nvidia.ko not found when booting and dropping to low graphics for this session.

Although I have got a working desktop, is there a way to restore, set up xorg.conf again for nouveau drivers?

Thanks

MrG

---

### Post by efflandt on 2010-07-05
Have you tried simply renaming xorg.conf to something else (cd /etc/X11, sudo mv xorg.conf xorg.conf.old).  By default there no longer is an xorg.conf unless you or something creates one.

---

### Post by MrGreen on 2010-07-05
I did look at xorg.conf and it was loading nvidia driver so moved it and thought xorg.conf.default would work.

Ok will remove it completely see what happens

Thanks

MrG

---

