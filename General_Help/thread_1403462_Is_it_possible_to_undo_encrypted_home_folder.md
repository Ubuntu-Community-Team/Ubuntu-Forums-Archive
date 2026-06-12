---
title: "Is it possible to undo encrypted home folder?"
date: 2010-02-10
forum: General Help
---

### Post by junglist313 on 2010-02-10
I recently did a clean install of Ubuntu 9.10 and when I did I chose to have /home on it's own partition and have it encrypted. The more I think about it the more I regret this decision. What if I want to switch distros down the road? What if I have to boot from a live cd to back up files? Is there a way to "undo" the encrypted home folder permanently? I don't mind having it on it's own partition, it's just the encryption that makes me worry.

---

### Post by jken146 on 2010-02-10
Basically the procedure would be this:

1. Copy all the files from /home to somewhere else.

2. Log out all users, become root.

3. Unmount /home

4. Format the partition that was mounted at /home such that it is not encrypted.

5. Mount it at /home (modifying the entry in /etc/fstab as appropriate).

6. Copy all the users' files back again.

---

