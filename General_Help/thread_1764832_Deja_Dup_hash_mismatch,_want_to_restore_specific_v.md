---
title: "Deja Dup hash mismatch, want to restore specific volume"
date: 2011-05-22
forum: General Help
---

### Post by ALF102 on 2011-05-22
I just backup my files. During restoration, there's a hash mismatch report. 
What I want to know is that, is there a way to restore certain files in the back up?
or is there are way to restore files by volume?

---

### Post by ALF102 on 2011-05-22
oops, looks like I found the solution. 
in terminal:

```
deja-dup --restore directory/file
```

or if you want the whole selected directory

```
deja-dup --restore directory
```

---

