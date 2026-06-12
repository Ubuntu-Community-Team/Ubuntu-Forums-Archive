---
title: "How do I make grep search with more directory depth?"
date: 2009-09-19
forum: General Help
---

### Post by rob86 on 2009-09-19
I know that grep "a string" * searches every file in the current directory, but how do I make it search every directory and its contents inside the current directory? Give it more search depth  I mean.

---

### Post by kaibob on 2009-09-19
Grep has a --recursive option that will do what you want. For example,

```
grep --recursive searchstring *
```

---

### Post by rob86 on 2009-09-19
Works good, thanks. I guess I didn't see that in the --help.

---

