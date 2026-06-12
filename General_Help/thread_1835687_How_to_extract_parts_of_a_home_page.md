---
title: "How to extract parts of a home page"
date: 2011-08-29
forum: General Help
---

### Post by ELMIT on 2011-08-29
Can anybody guide me to a starting point to solve that problem:

I need to extract a certain part of a web site between two certain defined markers on the page. Just as example from a home page I want to know all texts within a <h2> and </h2> tag.

---

### Post by bodhi.zazen on 2011-08-29
You can do this with sed, grep, awk, or perl depending on how complex you need to get.

```
grep '<h2>' index.html
```

---

