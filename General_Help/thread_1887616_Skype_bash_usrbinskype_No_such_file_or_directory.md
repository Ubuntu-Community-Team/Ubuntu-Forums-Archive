---
title: "Skype: bash: /usr/bin/skype: No such file or directory"
date: 2011-11-27
forum: General Help
---

### Post by Amurko on 2011-11-27
Skype has been working for 3+ years and now when I upgrade to the latest 2.2.035 in 64-bit Ubuntu 11.10, I get that message.  The skype binary clearly exists at that location.  What gives?

---

### Post by McNils on 2011-11-27
Not executable for some reason?
Look att the file with
ls -l /usr/bin/skype

---

### Post by oldos2er on 2011-11-27
Probably the multiarch bug, [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/852101?comments=all](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/852101?comments=all)

---

