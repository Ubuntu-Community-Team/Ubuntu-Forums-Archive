---
title: "Update Video Driver"
date: 2010-04-29
forum: General Help
---

### Post by mitchellcipriano on 2010-04-29
When the update with kernel -21 came out, my video driver would not work and I could not boot. I could select the old -19 kernel in grub and still boot. Now that the xorg-video-intel version 2:2.9.1-3ubuntu5 driver came out I was able to upgrade to it in the old -19 kernel and all works great. How do I use the recovery version of the new -21 kernel to load the new driver?

---

### Post by klemes on 2010-04-29
The upgrade is valid for all your available kernels.There is nothing that you need to do manually except boot with the -21 kernel and see if it 's now working for you.

---

### Post by mitchellcipriano on 2010-05-04
No, the -21 kernel will not boot. I updated to the -22 kernel, but it is also a no go. Is it possible that something became corrupt in the upgrade to -21 and that is now a problem for subsequent kernels, but not for th -19 kernel?

---

