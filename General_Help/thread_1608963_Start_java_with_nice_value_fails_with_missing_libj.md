---
title: "Start java with nice value fails with missing libjli.so"
date: 2010-10-29
forum: General Help
---

### Post by tombert on 2010-10-29
Hi all,

maybe someone has an answer to this.
In principle my java installation works perfect ... now I tried to increase priority with nice:

So I put special user rights to nice:
chmod u+s /usr/bin/nice

And then tried:
nice -n -20 java something

but this gives me the error that libjli.so is missing ... any ideas? It confuses me because nice shouldn't change search paths?? Or?

thx

---

