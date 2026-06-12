---
title: "Filter Results"
date: 2012-04-30
forum: General Help
---

### Post by gennatolls on 2012-04-30
Is there a way to filter results in Nautilus? If was looking for only *.doc files in a folder full of many file types what could I do?

I was looking for something similar the following in terminal:
```
ls *.doc
```Thanks,

---

### Post by chili555 on 2012-04-30
You might try:```
cd directory/in/question
ls | grep .doc
```

---

