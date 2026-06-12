---
title: "Checking status of file in terminal"
date: 2011-06-01
forum: General Help
---

### Post by salmontres on 2011-06-01
Hi guys,

How do I check if a file is a soft link in the terminal? They're usually color coded, but I gave permissions to a colleague and now every file is green. Is there a simple command for this?

---

### Post by zo3adams on 2011-06-01
ls -alG  will show files with much additional detail.  links will be followed by "-> the point they link to"

---

### Post by oldos2er on 2011-06-01
```
file <filename>
```

---

### Post by salmontres on 2011-06-01
Thanks Ann! That's exactly what I was looking for!

---

