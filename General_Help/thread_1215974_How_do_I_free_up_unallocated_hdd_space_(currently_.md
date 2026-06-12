---
title: "How do I free up unallocated hdd space (currently using gparted)"
date: 2009-07-17
forum: General Help
---

### Post by bizt on 2009-07-17
Hi,

I was attempting to have a dual boot of windows and linux on my laptop. Now, I set up the two partitions prior to re-installing both. I done this in windows. I installed windows on one and the other was for ubuntu. When I tries to install ubuntu on the free partition I run into problems anyway I just installed both side-by-side on the same partition originally intended only for windows, the idea was I would sort it out later .. like now.

Im using GParted as it was recommend to me from a linux user at my work. I can see the see space but it doesnt matter what partition I select it wont let me resize or maybe Im doing something wrong. Ive attached a screenshot so can see my setup. Does anyone have any experience of using this? What am I not doing? Should I maybe use another partition manager? Basically I just want to free up the unallocated space and give it all to Ubuntu (windows is just til I need it no more)

[ATTACH]121428[/ATTACH]

Any help would be much appreciated

Cheers
Bizt

---

### Post by michy99 on 2009-07-17
You need to run Gparted from a Live CD. You cannot change a partition while it is mounted. Also, you have to turn off swap.

---

### Post by michy99 on 2009-07-17
Another thing, sda5 and sda6 are logical partitions inside sda4, so you have to expand sda4 first.

---

