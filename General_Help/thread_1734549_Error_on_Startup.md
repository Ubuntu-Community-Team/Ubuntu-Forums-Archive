---
title: "Error on Startup"
date: 2011-04-20
forum: General Help
---

### Post by tunechi on 2011-04-20
hi , i was installing last night some applications , then i forgot to plugin my laptop so suddenly it turned off , anyways today i turned it on , while booting it gave me this error 
"error where found when mounting the disk file /"so i press I to ignore , and it works , but now how can i fix this error ??

thanks

---

### Post by daweefolk on 2011-04-20
It's just a guess, but maybe you should run a fsck on the disk. I believe you do that by running ```
sudo shutdown -F
``` (-F meaning force a fsck on reboot)

---

