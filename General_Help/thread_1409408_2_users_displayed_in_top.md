---
title: "2 users displayed in top"
date: 2010-02-17
forum: General Help
---

### Post by honey toast on 2010-02-17
Hi everyone, 
This may not be a big deal at all, but I notice that when I enter TOP into my terminal I can see that I have "2 users". How can I fix it to show 1 user? I did a search before posting and I did not find anything around the forum.

---

### Post by mk1w86 on 2010-02-17
There are two users shown because one is yourself and the other is root which runs various system processes.

If you look at the list of processes you will notice some are being run by your user and others by root. ;)

---

### Post by mcduck on 2010-02-17
There's nothing to fix, that's as it should be.

Two users doesn't mean two *different* users, it's just you logged in twice, once on your graphical desktop, and once in the terminal session where you are running the top. Each terminal session counts as it's own login session, so every terminal you have open adds one active user.

edit: If you want to, just run "who" to view all active users and where they are logged in:
```
mcduck@hyperion:~/ who
mcduck   tty7   2010-02-17 20:45 (:0)
mcduck   pts/0  2010-02-17 22:07 (:0.0)
mcduck   pts/1  2010-02-17 22:12 (:0.0)
mcduck@hyperion:~/
```
There you see me logged in on the desktop (tty7) and on two terminal emulators running inside that desktop (pts/0 and pts/1)

---

### Post by mk1w86 on 2010-02-17
Oops, I guess mcduck is right.

I just tried opening more terminal windows myself. :oops:

---

