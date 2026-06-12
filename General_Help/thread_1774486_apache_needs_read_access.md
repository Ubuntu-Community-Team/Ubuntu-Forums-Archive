---
title: "apache needs read access"
date: 2011-06-03
forum: General Help
---

### Post by lex1 on 2011-06-03
I am running apache2 on ubuntu 10.10
Apeche2 needs read access to certain files 

Is this the correct format of the file that apache needs 
read access to
-rw-r--r--

thanks

lex

---

### Post by SeijiSensei on 2011-06-03
They're called "[permissions]("http://www.perlfect.com/articles/chmod.shtml")," and, yes, having an "r" in the last triple makes a file readable by all users.

---

### Post by Habitual on 2011-06-03
> **lex1 said:**
> apache needs read access to -rw-r--r--


that's 644 

```
chmod 644 <file.ext>
```
As root **in the directory** that needs the file's permission changed.

---

