---
title: "Ubuntu Run Levels / States Question"
date: 2009-11-19
forum: General Help
---

### Post by Debik2 on 2009-11-19
Hi All,
 
I have a question I am hoping someone can answer for me. 
 
From what I can gather run level 1 and S are the same in that they are both single user maintenance/recovery modes, both are textual, both are in a down state and with both the file systems are mounted.
 
They are different in the fact that.... 
 
1 - kills
S - does not kill.
 
What is the purpose of having the S anymore?
 
I would love to have this clarified if anyone knows.
Thanks,
Deb

---

### Post by spiderbatdad on 2009-11-19
I believe init runlevels are only emulated in Ubuntu, and Ubuntu actually uses Upstart. Emulating runlevel s should be identical to 1, except that s acts as a system console, in 1 the file system is not mounted.

---

