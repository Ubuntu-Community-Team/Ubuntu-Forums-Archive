---
title: "file permissions issues"
date: 2006-02-12
forum: General Help
---

### Post by wilshire on 2006-02-12
i set up a dual boot system today. windows (xp) and linux (ubuntu).

it has a FAT32 partition, for sharing between the two systems, /dev/hda4, mounted at /shared.

file permissions for /shared are set such that it cannot be written to except by root. i cannot change this, even from the root account. 

i can change the permissions of /dev/hda4, and if it isn't mounted, i can change the permissions of /shared.

as soon as it's mounted though, the permissions of /shared revert back to 'root only' and i cannot change them, even as root. 

i've never run into this sort of thing before. what's going on?

---

### Post by aysiu on 2006-02-12
See the fourth link of my signature.

---

### Post by wilshire on 2006-02-12
that did it! 

thanks for the help. i thought finding the solution to that one was going to take some time.

---

### Post by aysiu on 2006-02-12
Glad it all worked out.

---

