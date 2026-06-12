---
title: "Auto Mounting with udev causes slow file transfer speeds?"
date: 2011-07-28
forum: General Help
---

### Post by cwhittier on 2011-07-28
I have my system configured in a way where nautilus is not running. I have added udev scripts/rules to handle auto-mounting USB drives, since nautilus isn't running to do it for me. I have noticed that after this change, file transfer speeds are significantly slower - averaging between 150kb and 800kb per second.

Does anybody know why this might be slow now?

---

### Post by cwhittier on 2011-07-28
Nevermind, after some more research, I solved my own problem.

I was mounting with the mount option sync, which is safer, but also slow as all hell. I changed the mount option to flush, which from what I have read, writes at the maximum possible speed.

Thanks everyone for all your help! lol.

---

