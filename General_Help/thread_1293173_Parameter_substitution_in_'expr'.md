---
title: "Parameter substitution in 'expr'"
date: 2009-10-16
forum: General Help
---

### Post by jmidgley on 2009-10-16
Hi

I'm starting down a long road to write myself a script, but stumbling rather early on.

Conditionally doing things depending on the age of a file comes into it so I've been playing with 'stat -c %Y somefile' and 'date +%s'.

I can subtract two dates:
expr `stat -c %Y somefile` - `stat -c %Y somefile2` 
which produces a number I can believe, but if I replace the minus sign with '<' (or >,<=, etc) I start getting very odd answers, like 1255733522. I only want a 'one' or a 'zero'! Strangely, '==' works, producing '0', but then I already knew the answer to that one...

What simple blunder am I making?

Cheers
John

---

### Post by jmidgley on 2009-10-17
I've just learned about 'escaping' reserved characters - of course '<' has a particular meaning on the command line, which isn't 'less than'.

On to the next problem.

John

---

### Post by StuartN on 2009-10-17
> **jmidgley said:**
> I've just learned about 'escaping' reserved characters - of course '<' has a particular meaning on the command line, which isn't 'less than'.

On to the next problem.

John

try these for numeric equality tests: -gt -lt -eq

---

