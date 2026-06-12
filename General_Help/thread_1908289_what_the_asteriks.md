---
title: "what the asteriks?"
date: 2012-01-13
forum: General Help
---

### Post by conradin on 2012-01-13
Im curious about how the shell (BASH) works, so I put in some stuff that I wouldn't normally put in, and got odd results. But how would I know what not to put in? Are these results to do with POSIX compliance? (or lack there of)?
```
$*
2011.jpg: command not found
$ ^
bash: :s^: no previous substitution
$ *.*
2011.jpg: command not found
$ *|*
2011.jpg: command not found
2011.jpg: command not found
$ ^*
^
^: command not found


```

---

### Post by nothingspecial on 2012-01-13
Hi, read this

[http://mywiki.wooledge.org/BashGuide/Patterns](http://mywiki.wooledge.org/BashGuide/Patterns)

---

