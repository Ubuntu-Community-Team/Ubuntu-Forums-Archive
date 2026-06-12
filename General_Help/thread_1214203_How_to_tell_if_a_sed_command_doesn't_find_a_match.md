---
title: "How to tell if a sed command doesn't find a match"
date: 2009-07-15
forum: General Help
---

### Post by timo1023 on 2009-07-15
I am writing a script where I am assigning a variable to the result of a sed search, but I would like the variable to be zero if the search doesn't find a match. I tried
```
blah=$(sed -n "/whatimlookingfor/p" || echo "0")
```
But that didn't work. Any ideas?

---

### Post by x22 on 2009-08-15
well, if you're searching for a given string, why not
use grep: it returns 0 on success, and 1 on failure:
"echo $?" to see the return values

---

