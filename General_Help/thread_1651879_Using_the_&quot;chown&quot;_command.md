---
title: "Using the &quot;chown&quot; command"
date: 2010-12-23
forum: General Help
---

### Post by sleapz on 2010-12-23
I've had to take ownership of a couple of directories where I've installed third party apps so that I can actually run/update them, but I noticed that when I used the command on a directory, "lock" icons appear on all of the child directories.  Can anyone explain why that is and how to avoid it?  If it's not avoidable, is it possible to mass select directories to change ownership from root to my account (if possible, is it wise?)?
Thanks for the help guys.

---

### Post by djeikyb on 2010-12-23
Probably none of the tree of directories belongs to you naturally. Chowning the first one doesn't change the status of the rest, because linux took you literally. To change the entire tree, use the recursive option: "chown -R".

---

### Post by sleapz on 2010-12-24
Awesome, thank you.

---

