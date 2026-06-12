---
title: "Boot error"
date: 2010-01-15
forum: General Help
---

### Post by Enigmapond on 2010-01-15
I've recently been getting an error right at the log-in screen stating the "/home/.dmrc if being ignored" and that it needs to be owned by user, which is me. How can I chmod this to change the permission, and why would this happen all of a sudden?

Thank you!

---

### Post by drs305 on 2010-01-15
I wrote a guide about this a while back. It explains the error message and how to fix it:

[Solving .dmrc and $HOME Permission Errors  ]("http://ubuntuforums.org/showthread.php?p=6161267")

If you ran a recursive chmod/chown command on your /home directory you may have altered some permissions or ownerships that the system doesn't like.


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by Enigmapond on 2010-01-15
Thank you! Nice tutorial and a quick fix!! Many thanks!

Cheers!

---

