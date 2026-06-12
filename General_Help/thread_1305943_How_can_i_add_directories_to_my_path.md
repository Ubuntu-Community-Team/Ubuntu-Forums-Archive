---
title: "How can i add directories to my path?"
date: 2009-10-30
forum: General Help
---

### Post by emigrant on 2009-10-30
hi,
i don't have a .bash_profile

if i do:

```
export PATH=$PATH:directory
```where does it go?
although it gets effected i don't see the path in .bashrc either.

ie.
if i want to add a directory manully what should i do?

thank you very much.

---

### Post by fragos on 2009-10-30
Add you PATH setting to .bashrc and it will work for that user only.

---

### Post by emigrant on 2009-10-30
How to add manualy?
Iv exported a new path and is effective. But grep cnt find it in .bashrc

---

### Post by jackachan on 2011-05-11
Just type 
export PATH="$PATH:your_path" 

in the .bashrc file.

Adding into the .profile works as well.

Of course, remember to source the file after modification.

source .bashrc

---

