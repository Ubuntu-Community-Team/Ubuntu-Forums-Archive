---
title: "cd from symbolic link to the real directory"
date: 2010-09-24
forum: General Help
---

### Post by legendbb on 2010-09-24
Hi, all,

Is there a way to cd directly from a symbolic link to the real absolute directory?

Thanks,
:confused:

---

### Post by WorMzy on 2010-09-24
'cd -P <symlink>' will take you to the symlink's "real" directory instead of the relative directory.

---

### Post by legendbb on 2010-09-27
Thank you very much, especially when there is no man for cd.

---

### Post by QLee on 2010-09-27
> **legendbb said:**
> Thank you very much, especially when there is no man for cd.
It's a shell builtin command, you can find it in the bash manual.

---

