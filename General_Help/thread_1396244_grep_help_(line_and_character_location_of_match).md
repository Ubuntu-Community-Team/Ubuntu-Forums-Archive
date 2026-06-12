---
title: "grep help (line and character location of match)"
date: 2010-02-01
forum: General Help
---

### Post by patmanpato on 2010-02-01
Hi all,
I was wondering if there is a way to search a file for a specified pattern, and return the pattern plus its line location AND character location (within that line).

The pattern I'm using (for egrep) is:

egrep -o "(&#|%u)[0-9|a-fx]{4,} -n

which prints out things like
1:<some match>
23:<some match>

What would be nice would be something like:
1:1:<some match>
23:5:<some match>

Can (e)grep or any other tools give such a result?


Thanks for any help. :popcorn:

---

