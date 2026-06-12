---
title: "Bash shell script: What is the difference between $* and $@ ?"
date: 2009-11-12
forum: General Help
---

### Post by dandeliondream on 2009-11-12
I understand $* will take in all the positional variables. I do not understand what $@ means?
 
Please advise.

---

### Post by lswb on 2009-11-12
It has to do with how the arguments are concatenated together and quoted in the resulting list.

$@ lists all arguments as "$1" "$2" "$3"   etc.

$* lists them as "$1 $2 $3 $4" 

(If you change $IFC then instead of a space between args in $* the first character of $IFC will be used)

---

