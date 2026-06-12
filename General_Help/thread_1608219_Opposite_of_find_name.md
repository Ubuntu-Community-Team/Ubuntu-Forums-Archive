---
title: "Opposite of find name"
date: 2010-10-28
forum: General Help
---

### Post by wesg on 2010-10-28
What is the secret to searching for the opposite of the find request? Ie. I'm looking for files with a file extension NOT equal .PNG

```
find . -name "*.png"
``` 

works to find the opposite of what I want. Suggestions?

---

### Post by gmargo on 2010-10-28
The man page for **find** reveals the '!' (bang or exclamation mark) as a negation.  It must be escaped or quoted to prevent interpretation by the shell.
```

find . -type f '!' -name '*.png' -print

```

---

### Post by wesg on 2010-10-28
Perfect! Thanks gmargo

---

