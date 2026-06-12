---
title: "What if I mount to a full directory?"
date: 2010-10-01
forum: General Help
---

### Post by UncleBoarder on 2010-10-01
I've moved my /home to a second internal drive.  And I've done it properly by creating an empty /home on the root file system and mounting the new home to that empty directory.  But...

While I was making all that work, I think a made a mistake once and left the original /home in place and mounted to it anyway.  It worked.  And when I deleted a directory on the new home I expected to be able to find it on the old home when I unmounted the second drive.  But I didn't, it was gone too.

So, my question... If I were to leave it like that... /home intact on my root filesystem, AND a copy of /home on my second volume mounted over the top of the original /home...

Would that effectively give me a backup?  I mean if drive 2 failed, would the original /home still be intact?

---

### Post by psusi on 2010-10-02
No.  Whatever is in the directory is just hidden until you unmount what you mounted over top of it.  Changes to one disk have no effect on the other.

---

