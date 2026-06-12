---
title: "right padding in echo of shell script"
date: 2010-03-22
forum: General Help
---

### Post by killthemyth on 2010-03-22
I'm a n00b in shell scripting, please help me: 

echo "$num $den $file" is the current format
I need 10 right padding for each term above in the above where $num  & $den is of %d type, whereas $file is %s type.
 
Thanks in advance

---

### Post by rnerwein on 2010-03-22
hi
do you need something like:
printf "%5d  %5d %20s\n" $num $den $file

ciao

---

### Post by killthemuth on 2010-03-22
yes

---

