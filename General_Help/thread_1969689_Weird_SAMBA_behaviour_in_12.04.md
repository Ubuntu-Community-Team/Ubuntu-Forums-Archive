---
title: "Weird SAMBA behaviour in 12.04"
date: 2012-04-30
forum: General Help
---

### Post by VanCardboardbox on 2012-04-30
Casual user here. I am seeing SAMBA behaviour that I have not seen before on a new install of 12.04 (w/GNOME Shell 3.4) on my main desktop machine. I multi-boot and this new install sits along side an exsisting install of 11.10 (w/GNOME Shell 3.2). 

There are a number of shared directories on the desktop. I have SAMBA and fstab set up identically on both 12.04 and 11.10 and am attempting to connect to shared dirs from a notebook running 12.04.

If I boot the desktop into 12.04 and then, on the notebook, run **mount -a** it will not mount the share dirs. If I boot the desktop into 11.10 the notebook mounts the SAMBA shares just fine. The weird part is that once I have mounted the desktop's shares while its in 11.10, then restart and boot into 12.04, the shares remain mounted on the notebook and I can access all files on all shares. I can reproduce this behaviour accessing the desktop shares with my android phone. 

So the problem is not the actual share, but the authentication?

---

### Post by VanCardboardbox on 2012-04-30
This problem has been resolved, but not through any action on my part. After repeating the behaviour I described in my OP umpteen times over a day-and-a-half, it simply stopped. I am pleased, but puzzled.

---

