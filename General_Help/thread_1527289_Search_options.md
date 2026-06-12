---
title: "Search options"
date: 2010-07-09
forum: General Help
---

### Post by dcollier on 2010-07-09
Hello all, i am trying to figure out a way to search a file for a particular string, but I want the result to display lets say 3 lines above the search results and 3 lines below the search results.  I'm not sure if this would need to be done with an if statement or what, but any suggestions would be appreciated.

---

### Post by ankspo71 on 2010-07-09
Hi, 
try this:
```
cat FILENAME | grep -n -B 3 -A 3 SEARCHTERMS
```

-n = show line numbers (optional but useful)
-B 3 = Show 3 lines before
-A 3 = Show 3 lines after

---

### Post by dcollier on 2010-07-13
Thanks I will give that a try :D

---

### Post by dcollier on 2010-07-13
you are the man ankspo, it worked like a charm!!!!

---

### Post by HermanAB on 2010-07-13
fgrep

---

