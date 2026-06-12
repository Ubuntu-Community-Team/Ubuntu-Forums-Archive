---
title: "ApArmor- necessary?"
date: 2009-08-23
forum: General Help
---

### Post by oboedad55 on 2009-08-23
I have AppArmor installed by default in Jaunty. Is this something I need? I don't run a server or do any networking other than connecting to the Internet. Any direction would help. :shock:

Jon

---

### Post by 3rdalbum on 2009-08-23
It's safest to leave AppArmour as it is; it doesn't get in the way and it does provide some protection against unknown attacks. It barely uses any system resources either.

I'm sure you can remove it without problems, but you really might as well leave it there.

---

### Post by zika on 2009-11-30
If You do not want AppArmor to start just add apparmor=0 to Your kernel boot line.

---

