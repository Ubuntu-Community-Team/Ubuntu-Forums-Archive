---
title: "XFS destroys files ?"
date: 2011-09-23
forum: General Help
---

### Post by Nuvielle on 2011-09-23
Sry that i dig out that old Thread, but i have a Question here.

If you disable the write cache and then add nobarrier in /etc/fstab wouldn't that reduce Posibility to damage files, cause the kernel don't holds the data back from writing any more and nothing in the writecache could get lost any more ( since he isn't used )

And i think it would be faster too , cause the barrier is known to make xfs a little bit slower. Does we lose spead through disable write - caching ?

I personaly think not, ive testet it on my system and it feels much snappier since this ^^

---

### Post by oldos2er on 2011-09-23
I've moved your post to its own thread. Rather than post in an old thread, it's usually a good idea to create a new one. You can add a link to the old thread if you feel it's helpful.

---

