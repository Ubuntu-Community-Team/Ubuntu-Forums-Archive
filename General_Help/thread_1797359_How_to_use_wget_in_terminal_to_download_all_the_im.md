---
title: "How to use wget in terminal to download all the images in a web page"
date: 2011-07-04
forum: General Help
---

### Post by kka147258 on 2011-07-04
Rt

---

### Post by An Sanct on 2011-07-05
Utilize a bash script :)

[read more...]("http://www.linux.com/archive/feed/59457")

and some [more ...]("http://lifehacker.com/161202/geek-to-live--mastering-wget")

---

### Post by Habitual on 2011-07-05
```
wget -r -l1 --no-parent -nH -nd -P/tmp -A ".gif,.jpg" http://example.com/images 
```

---

