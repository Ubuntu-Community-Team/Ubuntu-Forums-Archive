---
title: "How 'cd' to parent of symbolic link?"
date: 2010-12-29
forum: General Help
---

### Post by Pithikos on 2010-12-29
I have a symbolic link "ircc" which links to a directory deep deep in the nasty system. I use ```
cd ircc
``` to get in that wild place. How can I then cd to the actual parent of that place? 
```
cd ..
``` Just puts me in the parent folder of the symbolic link :/

---

### Post by Vaphell on 2010-12-29
cd -P ..

---

