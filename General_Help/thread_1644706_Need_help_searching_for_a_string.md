---
title: "Need help searching for a string"
date: 2010-12-13
forum: General Help
---

### Post by knottshawk on 2010-12-13
So I'm wanting to search my entire filesystem for part of a string... I'm looking for the following, which is part of a directory path: ".temp/filename.txt"

I've tried the following, from the root of the system:

grep -r ".temp/filename.txt" *

It returns dev/log and the optical drive with "No such device or address" or "No medium found" and then it acts like it's still searching, but it's either EXTREMELY slow, or it's not doing anything at this point. I thought this would tax the processor, but it's not... plus if I search processes, nothing seems active.
 Am I doing something wrong here?

---

### Post by jim_deadlock on 2010-12-13
This is normal behaviour for what you're doing - grepping your entire file system will take forever and the grep process will not take a lot of cpu. Plus you're running the process under your local user so it won't be able to search a lot of stuff.

---

### Post by knottshawk on 2010-12-13
k... wasn't sure about the CPU taxation... I did prepend sudo onto my latest attempt, so it should be good to go.

---

