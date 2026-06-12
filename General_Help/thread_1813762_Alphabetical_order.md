---
title: "Alphabetical order"
date: 2011-07-28
forum: General Help
---

### Post by dilshat on 2011-07-28
Hi,
How is the alphabetical order in ubuntu? Is the oder:
a,b,...,z,A,B,...,Z
or
a,A,b,B,...,z,Z
????????
Because when I tried to list file like
1.ls [a-z]*.txt
  result was
  a.txt A.txt b.txt B.txt
2.ls [A-Z]*.txt
  result was
  A.txt b.txt B.txt
so I can't list all files which begin with capitals
this problem has been encountered only in ubutnu, in fedora or other dist. the globbing was fine as desired.
any Help plz
Thanks

---

### Post by Lars Noodén on 2011-07-28
egrep will help.  Try

```

ls *.txt | egrep "^[A-Z]"

```

---

