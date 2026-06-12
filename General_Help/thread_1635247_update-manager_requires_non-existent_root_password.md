---
title: "update-manager requires non-existent root password"
date: 2010-12-01
forum: General Help
---

### Post by Brandon Williams on 2010-12-01
One of my machines running 10.04 recently began requiring the root password in order to carry out privileged operations in update-manager. I found [this bug](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/664302) in launchpad. It's similar, but related to 10.10. If I create a root password, then I can use it to carry out privileged operations in update-manager, but I prefer not to add a root password just for this purpose.

Has anyone else seen this problem? And if so, did you find a solution?

PS: I searched for related threads in the forums but found none. If you are aware of a related thread that I missed, please just point me in that direction.

---

### Post by coffeecat on 2010-12-01
Long shot this, but have a look in gconf-editor, apps > gksu. Make sure the sudo-mode box is ticked.

**EDIT:** Oops, just noticed you are using Xubuntu. I know that Xfce uses some gtk stuff but I don't know whether it also has a gconf-editor as in gnome.

---

### Post by Brandon Williams on 2010-12-01
Thanks for the suggestion. That was the problem!

I looked at the setting again today just because of a suspicion that I might have looked at the wrong machine the first time, and sure enough, I had. In fact, the sudo-mode setting was unchecked after all, and clicking the box solved the problem.

Thanks again!

---

