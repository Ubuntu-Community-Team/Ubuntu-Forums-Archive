---
title: "Disk Usage"
date: 2010-02-25
forum: General Help
---

### Post by theozzlives on 2010-02-25
Is there a CLI version of the Disk Usage Analyzer?

---

### Post by blueridgedog on 2010-02-25
Try:

```
df
```

or, if you want usage:

```
sudo du --max-depth=1 | sort -g
```

---

### Post by chalewa on 2010-02-25
```
df -H 
```

is probably a better option.

---

