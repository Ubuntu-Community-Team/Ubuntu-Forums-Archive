---
title: "Breeding linux boot entries in Grub 2 [Ubuntu 9.10]"
date: 2010-03-08
forum: General Help
---

### Post by RexButler on 2010-03-08
[LEFT]Recently I installed Ubuntu 9.10 on my system (beside Windows 7) to provide a better environment to enhance my programming skills.  I am a relative novice at unix/linux.

At the time of install, there was one boot entry for Ubuntu Linux and one for memtest.  These 2 (in order AB) have now multiplied 4 and then 6 (in order ABABAB).  I believe this duplication occurs after automatics software updates.


Rex
[/LEFT]

---

### Post by whoop on 2010-03-08
This is normal. You can remove them manually, with synaptic for instance (search for linux-image).

I advise you to keep at least two of the most recent working kernels on your system, as you never know. I have two, if that comforts you :D

---

