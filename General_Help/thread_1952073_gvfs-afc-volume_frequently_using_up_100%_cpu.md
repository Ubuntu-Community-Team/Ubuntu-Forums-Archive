---
title: "gvfs-afc-volume frequently using up 100% cpu"
date: 2012-04-03
forum: General Help
---

### Post by IsmAvatar on 2012-04-03
I'm running Ubuntu 11.10 (2 users, each with a user account), and I also have an iPod Touch which I occasionally plug in (pretty much for the sole purpose of recharging).

As a result, I'm frequently encountering extreme sluggishness of my desktop during normal non-intensive usage, which is unusual since I have 4 gHz dual-core processor with 6 GB of RAM.

Going into the terminal and typing `top` reveals the culprit:
gvfs-afc-volume is using 100% cpu. I kill the process, and suddenly everything is running smooth again. At least until the next time.

Any way to stop it from doing this? I've read up on it a little, and found reports going back to 9.04, mostly just saying "don't uninstall it because it's for your ipod".

---

