---
title: "Test password againt a file."
date: 2010-12-25
forum: General Help
---

### Post by SpinningAround on 2010-12-25
I got a .mqv file, that is encrypted with a password. I would like to test passwords against this file using shell. Question is how I try a password and how I know if it was successful or not.

Mime info:
```
file.mqv: application/zip; charset=binary
```

---

### Post by WorMzy on 2010-12-25
This is a shot in the dark, but try unzip

```
unzip -P PASSWORD /path/to/file.mqv
```

---

