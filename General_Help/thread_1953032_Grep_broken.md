---
title: "Grep broken"
date: 2012-04-05
forum: General Help
---

### Post by Jeroen De Dauw on 2012-04-05
When I am in a directory with a bunch of files of which some have the letter 'a' in them, and I do

> grep a *

I do not get any results. Am I doing it wrong, or is it indeed broken as I suspect? And if this is supposed to work, then why might it not be working, and what might fix it?

---

### Post by raja.genupula on 2012-04-05
```
grep 'a' *
```

do that .

---

### Post by Jeroen De Dauw on 2012-04-05
Also tried that.

Found the problem. There was an executable file named grep in a dir included in my path. An empty file :)

---

