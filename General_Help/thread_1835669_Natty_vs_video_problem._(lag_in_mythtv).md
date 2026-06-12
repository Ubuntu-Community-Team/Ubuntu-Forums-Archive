---
title: "Natty vs video problem. (lag in mythtv)"
date: 2011-08-29
forum: General Help
---

### Post by Kheops_74 on 2011-08-29
Since the kernel 2.6.38-11-generic some mpeg video that i recorded in mythtv are laggy. I see this message in the mythfrontend log:


2011-08-29 18:42:19.465 ALSA, Error: Error opening /proc/asound/card1/pcm0p/sub0/prealloc. Fix reading permissions.
2011-08-29 18:42:19.465 ALSA, Error: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely

I saw somewhere that i must do the command : sudo echo 128 > /proc/asound/card1/pcm0p/sub0/prealloc. 

This file "prealloc" is not existing on my computer and it don't want to create it. I change permission to the folder without success. 

Any Idea to create the file?

Any other idea to solve the issue?

---

### Post by Kheops_74 on 2011-08-29
Computer crash when flash video are playing for a while. What they did wrong in the kernel update?

---

### Post by Kheops_74 on 2011-08-31
Nobody knows  /proc/asound/card1/pcm0p/sub0/prealloc file? Do you have it on your Natty system?

---

