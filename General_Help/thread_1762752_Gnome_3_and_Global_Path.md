---
title: "Gnome 3 and Global Path"
date: 2011-05-19
forum: General Help
---

### Post by slooksterpsv on 2011-05-19
I use Gnome 3 not Unity, and the PATH variable is not set correctly. When trying to execute programs that are in like /usr/games it says it can't execute child process. Upon opening terminal the only thing in the PATH is:

/usr/local/bin:/usr/bin:/bin

I've tried to do some recursive searches to find where its setting that variable and I can't figure it out. Nor do I know how to change the global PATH for users in Gnome 3. I've added path items to rc, rc.local, rcS, etc. nothing's worked.

Anyone have an idea?

---

### Post by slooksterpsv on 2011-05-19
Ok so the workaround to it is, add:
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
to .profile

It looks like a bug with gnome 3

---

