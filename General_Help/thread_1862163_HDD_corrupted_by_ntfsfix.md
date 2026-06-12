---
title: "HDD corrupted by ntfsfix"
date: 2011-10-16
forum: General Help
---

### Post by subehsharma on 2011-10-16
I initially had this problem with my Maxtor HDD that everything in it was "read-only". While searching for the solution i came across a post on ubuntuforums which mentioned this command:


sudo ntfsfix /dev/sbc1


Without thinking much, i gave it a try but after this, my HDD stopped getting detected. When i boot into windows, it shows the drive as corrupted and asks for a format.

I've more than 300gigs of data in it. Could there be something we can do?

i can't even see it listed in the below output:


subsharm@subsharm:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             22973308   5016428  16789880  24% /
udev                   1003376         4   1003372   1% /dev
tmpfs                   404516      1008    403508   1% /run
none                      5120         0      5120   0% /run/lock
none                   1011288       956   1010332   1% /run/shm
/dev/sda1             73366524  45974760  27391764  63% /media/System

---

### Post by subehsharma on 2011-10-16
bump...anyone?

---

