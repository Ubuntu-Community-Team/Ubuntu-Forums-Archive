---
title: "ls issue"
date: 2011-09-04
forum: General Help
---

### Post by raja.genupula on 2011-09-04
i don't know is this correct category about posting this 

guys is there any one who had tried this 

look at my image 
ls & l both are behaving same :lolflag:

---

### Post by debd on 2011-09-04
that's because an alias for ls is set by default in Ubuntu's ~/.bashrc file.
its ```
l='ls -CF'
```
where -C tells ls to list entries by columns and -F tells it to append an indicator after file/dir names like a * for executable files, / for directories and so on..

---

### Post by raja.genupula on 2011-09-04
thanks for this man .

---

