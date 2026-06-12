---
title: "awk: get rid lines in a tab-separated-file with empty entries"
date: 2011-04-14
forum: General Help
---

### Post by lethalfang on 2011-04-14
So, I can get rid lines where a particular entry in the 100th column is "**NA**,", i.e., 

```
cat file.csv | awk -F "\t" '$100!="**NA**"' > new_file.csv
```

But how do I do it when the entry is an empty one?

Thanks.

---

