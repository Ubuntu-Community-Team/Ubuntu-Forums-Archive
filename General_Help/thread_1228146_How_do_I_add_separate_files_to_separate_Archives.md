---
title: "How do I add separate files to separate Archives"
date: 2009-07-31
forum: General Help
---

### Post by Theholylancer on 2009-07-31
Hi guys, I wanted to know if there is a way to add separate files to separate archives (.tar.gz ones) with ubuntu, either with command line or with the GUI.

For example if you have files in /home/asdf:

a.asdf
b.asdf
c.asdf
e.asdf
f.asdf

with one command you then make them all into separate archives in say another spot on the machine 

in /home/asdfbackup

a.asdf.tar.gz
.
.
.
f.asdf.tar.gz

how would I be able to do this, without actually write a script to accomplish it.

Thanks a bunch

---

### Post by sisco311 on 2009-08-01
Hi and welcome to the forums!

You can use the [find]("https://help.ubuntu.com/community/find") command:
```
find  /home/asdf -name "*.asdf" -exec tar zcvf " /home/asdfbackup/{}.tar.gz" "{}" \;
```

---

### Post by Theholylancer on 2009-08-04
sweet thanks

---

