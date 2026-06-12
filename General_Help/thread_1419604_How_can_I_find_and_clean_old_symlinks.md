---
title: "How can I find and clean old symlinks?"
date: 2010-03-02
forum: General Help
---

### Post by kansasnoob on 2010-03-02
I recently tried the package "pysdm" to mount a data partition but didn't care for the way it handled things so I opted for editing fstab which I'm much more satisfied with :D

I did then purge pysdem and it's config files but something lingered, finally I got things working by using a UUID designation in fstab but I know there's an old symlink to a /dev/sdb7 that has since been deleted and later recreated with a new UUID. 

I have "googled" enough to find that the package "fslint" should be able to handle this but since one gui got me in trouble I'm reluctant to use another, I'd prefer just being able to find where symlinks live and ripping them out by the short hairs :P

---

### Post by kansasnoob on 2010-03-03
Bump :D

Maybe some fresh eyes today, there is no urgency as things are working fine, I'd just like to keep things clean.

---

### Post by kansasnoob on 2010-03-03
Just tried fslint on Hardy and cleaned a few old symlinks. All seems well, I'll report more as I learn more :)

---

