---
title: "WMV files"
date: 2011-01-08
forum: General Help
---

### Post by cowboy7305 on 2011-01-08
I have down loaded a movie but its come in about 5 WMV files what can i do to join them together many thanks

---

### Post by TeoBigusGeekus on 2011-01-08
```
mencoder -oac copy -ovc copy -o NameOfFinalFile.wmv file1.wmv file2.wmv file3.wmv file4.wmv file5.wmv
```

---

