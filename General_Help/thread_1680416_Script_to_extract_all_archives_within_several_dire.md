---
title: "Script to extract all archives within several direcotires?"
date: 2011-02-02
forum: General Help
---

### Post by Klump on 2011-02-02
Hello,

I've never really used command line to do such things but I'd like to learn. So, how do I extract all archives that are spread across several directories in one go?

For instance:
> Work/
Work/Today/a.rar
Work/Tomorrow/b.rar
Work/Yesterday/c.rar

Cheers :)

---

### Post by AlphaLexman on 2011-02-02
I don't have rar on my machine so I can't test this but it should work.```
cd Work; find . -name "*.rar" -execdir rar {} +
```

---

### Post by Klump on 2011-02-02
Thank you.

---

