---
title: "Strange Monitor Problem with 9.10"
date: 2010-02-04
forum: General Help
---

### Post by Tykeboy on 2010-02-04
I have 9.10 installed on a desktop PC which is 6 years old. I recently upgraded from 9.04 which worked fine. Now, however, there is a strange problem with the monitor (old CRT type). When you try to login, the monitor does a couple of resolution changes and the system goes back to the login page. I can get in in recovery mode and I can see the system doing the resolution changes in Xorg.0.log.old. I tried it with a TFT TV which has a VGA input and it successfully logged in but with a reduced screen resolution (480x320) and wouldn't let me change it. Also if I power off the CRT monitor while logging in, it gets in with the same low-res setting.

Anyone else had this problem?

Many thanks.

---

### Post by chewearn on 2010-02-05
It looks like the auto-detection failed, that's all.

Therefore, you would need to specify the resolution manually.

---

