---
title: "Recover after destroying the /home partition"
date: 2009-12-18
forum: General Help
---

### Post by theabsurd on 2009-12-18
Hi

In an attempt to solve lacking space problem, I foolishly formatted what used to be the /home partition of ubuntu and merged it with another windows partition.

Naturally ubuntu can't load after I log in. Can I somehow relocate "home" to some directory on the ubuntu's system drive. Please tell me how.

Thank you

---

### Post by oldfred on 2009-12-18
Your /etc/fstab is probably still looking to mount the /home partition which does not exist. I think if you just delete the incorrect fstab line, it will automatically create a new default /home in root. Then you can deal with moving home or linking data into your home.

---

### Post by theabsurd on 2009-12-18
oldfred, deleting the line in /etc/fstab and creating a new user from a failsafe terminal session worked (by worked I mean that I was able to see the graphical desktop). However this new user that was just created has limited administrative rights. Where to go from that is probably a whole different question.

Thank you!

---

