---
title: "I think my /var/lib/dpkg/status is corrupt."
date: 2012-07-12
forum: General Help
---

### Post by CLCressman on 2012-07-12
I am running Precise. Is it safe to replace /var/lib/dpkg/status with /var/lib/dpkg/status-old? Or is there a better way to recover from this problem?

I think that this is related to [http://ubuntuforums.org/showthread.php?t=2023060](http://ubuntuforums.org/showthread.php?t=2023060)

Thanks for your consideration.

---

### Post by ranger1021994 on 2012-07-13
I think its related to current packages installed.
It should be safe but your the -Old might not contain recently installed packages
So expect new packages to go orphan maybe.

---

### Post by CLCressman on 2012-07-17
Here is what I did: 
I have an installation of 11.10 on a USB drive, so I booted into that. Fortunately I had *Meld* installed there. I opened */var/lib/dpkg/status *and* /var/lib/dpkg/status-old,* from my 12.04 install, with *Meld*. The last part of *status *was missing. After looking at the differences I thought that I could update *status-old* with *status.* So I made what seemed to be logical edits, and now it seems to be working. :)

---

