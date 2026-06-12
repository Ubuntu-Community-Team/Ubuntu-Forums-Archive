---
title: "Migrated to new hardware, now system will only boot through recovermode &gt; resume"
date: 2012-01-07
forum: General Help
---

### Post by a person on 2012-01-07
Last week, my motherboard decided to eat up all my ram.  This prompted me to pick up new hardware.  I went from a amd cpu to an intel, and a nvidia card to a nvidia card.  My issue is (which I had once before, but never fixed) is that my system will not boot normally.  To get my system to boot, I have to enter recovery mode, and hit resume.  That's it; it works as expected after that.

Does anyone know what is causing this, and/or how to fix it?  I'm guessing it has to do with the bootsplash, as that gets skipped when I enter recovery mode.

---

### Post by 2F4U on 2012-01-07
It should be easy to verify that theory by removing "quiet splash" in /etc/default/grub and running

sudo update-grub

after that.

---

