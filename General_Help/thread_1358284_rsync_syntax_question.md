---
title: "rsync syntax question"
date: 2009-12-18
forum: General Help
---

### Post by change_mode on 2009-12-18
I want to back up 6 folders using rsync. Is there a way to do this with only one command?

Example: I want folders A, B, C, D, E and F backed up. With cp it would be:

```
cp A B C D E F DEST
```

Is there a way to do something like this with rsync?

---

### Post by StuartN on 2009-12-18
> **change_mode said:**
> ```
cp A B C D E F DEST
```

Is there a way to do something like this with rsync?

You could spoof it by **rsync**ing a directory with links to A B C D E and F within it.

---

### Post by change_mode on 2009-12-18
That's a good alternative way to do it I guess.

I'm still surprised though that rsync with its 1000 options can't do this without using such tricks.

---

