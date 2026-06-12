---
title: "Hard links ?deprecated? rumour?"
date: 2010-02-16
forum: General Help
---

### Post by Primefalcon on 2010-02-16
I heard a rumour that creating hardlinks via ln have been deprecated in Ubuntu, can someone tell me this isn't so? I use them all the time, especially with organizing files via folders where a file belongs in multiple categories but I don't want to have multiple copies of said files on hard drive due to space

---

### Post by vanadium on 2010-02-16
The rumour is probably wrong. Hard links can sometimes render file management difficult. Backing up takes more time when hardlinks need to be recognized and preserved. In many cases, softlinks can fulfill the needs and are more transparent: you know that you can delete the symbolic link. with hard links, beware that the instance you delete is not the last one.

---

### Post by Primefalcon on 2010-02-16
true but ls -l shows how many hard links there are to a file. And if you do want to delete every file you can simply use 

```
find /mountPoint -samefile filename
```

So not too complicated, and tbh I find symbolic links for a pain, since you have to be careful about moving the original hard link since that'd break symbolic links

---

