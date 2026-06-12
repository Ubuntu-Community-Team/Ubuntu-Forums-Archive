---
title: "new 2TB drive, need to &quot;burn-in&quot;"
date: 2010-11-12
forum: General Help
---

### Post by egalvan on 2010-11-12
Just received a new 2TB drive.
is there a piece of software or script that will burn-in or exercise a hard drive?
I want to stress it for a week or two before committing  data to it.

---

### Post by bioterror on 2010-11-12
Maybe this could be the thing:
[http://www.coker.com.au/bonnie++/]("http://www.coker.com.au/bonnie++/") It can be installed from the normal ubuntu repos.

---

### Post by bioterror on 2010-11-12
And one thing could be playing with
```
~$ cat /dev/urandom > /media/harddrive/
```
and making a script which runs that cat, deletes, and all over again.

---

