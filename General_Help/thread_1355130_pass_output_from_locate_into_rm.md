---
title: "pass output from locate into rm"
date: 2009-12-14
forum: General Help
---

### Post by pythonscript on 2009-12-14
How do I pass the output from locate into the rm program? I'd like to locate all of a certain file and remove it (using rm or rm -f). I tried

```
locate Thumbs.db | xargs rm
``` but because many of the directories have spaces in the name, I get a slew of "No such file or directory" errors because it's treating each word in the title as a separate name. 

Thanks for the help!

---

### Post by sisco311 on 2009-12-14
```
locate Thumbs.db | xargs -d '\n' rm
```

---

### Post by pythonscript on 2009-12-14
Thank you; that does exactly what I need it to do.

---

