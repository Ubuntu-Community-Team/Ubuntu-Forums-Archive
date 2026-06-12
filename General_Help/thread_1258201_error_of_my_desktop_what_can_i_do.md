---
title: "error of my desktop what can i do?"
date: 2009-09-04
forum: General Help
---

### Post by follo95 on 2009-09-04
i have a problem when i start my ubuntu there is a figures than say than there is an error of my desktop this error belong to the 644 command 
what can i do for this???
please help me
and sorry for my english but i am italian

---

### Post by Vaphell on 2009-09-04
ownership/rights issues?
does it say anything specific, for example what exactly has that problem?

check if files/directories are owned by you and if you have read/write/execute permissions on them
ls -l

644 = rw-r--r-- (read/write for you, read for group, read for everybody else)

---

