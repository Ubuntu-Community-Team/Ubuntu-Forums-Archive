---
title: "Output sort"
date: 2011-12-05
forum: General Help
---

### Post by smasher40 on 2011-12-05
Hi

One question is there any comand to sort the information grabbed from a file???

My teatcher asked me to extract from an HTML file the Operating systems that were in a table so i did with the the following command:

grep 'TD_WIDTH' OSs.html | tr -s '>' '#' | cut -f3 -d# | head -5 | tail -4

and the output was :

windows
MAC OS X Power PC
MAC OS X intell
Lnux

then he told me to sort that output

is there any command for that?? or it must be an argument of any other known command that i already performed in that operation.

Thanks once again for your patience

Paulo

---

### Post by phidia on 2011-12-05
There is a sort command in bash. For a list of those see [this page]("http://ss64.com/bash/"). Is your teacher actually expecting you to get your answers at a forum? Anyway sort -h should give you some ideas, and yes it would be an argument to sort.

---

