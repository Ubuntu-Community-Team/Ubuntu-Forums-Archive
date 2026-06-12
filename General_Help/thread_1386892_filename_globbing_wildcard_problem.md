---
title: "filename globbing wildcard problem"
date: 2010-01-21
forum: General Help
---

### Post by glaucomag on 2010-01-21
Hi, I think that there is a problem on UBuntu 9.10 about filename globbing. I tried on Red Hat and it's ok. I don't understand because I think that bash is the same on all Linux distributions, isn't it? Look you too:

1) user@host:~/test$ ls
aldo  Aldo  giacomo  Giacomo  giovanni  Giovanni
# directory
2) user@host:~/test$ ls [A]*
Aldo
# correct!
3) user@host:~/test$ ls [a]*
aldo
# correct!
4) user@host:~/test$ ls [a-b]*
aldo  Aldo
# wrong!!! "Aldo" not good
5) user@host:~/test$ ls [a-g]*
aldo  Aldo  giacomo  giovanni
# wrong!!! "Aldo" not good
6) user@host:~/test$ ls [a-h]*
aldo  Aldo  giacomo  Giacomo  giovanni  Giovanni
# wrong!!! "Aldo", "Giacomo" and "Giovanni" not good

Can you help me? Thank you.

---

### Post by glaucomag on 2010-01-21
I thought that this question was very simple for you .....
Can you try to do it?
I'd like to know al least if the problem is only mine.

Thanks

---

