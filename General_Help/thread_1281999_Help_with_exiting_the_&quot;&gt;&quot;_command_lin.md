---
title: "Help with exiting the &quot;&gt;&quot; command line"
date: 2009-10-03
forum: General Help
---

### Post by Alan Morgan on 2009-10-03
I am new to UNIX and Ubuntu and occassionally hit a wrong command and get the line that looks like this:

>

How do I get out of it?

A

---

### Post by fela on 2009-10-03
When you want to exit a program immediately in the terminal, or if it isn't responding, type Ctrl + C. If that doesn't work, type Ctrl + Z (both *should* work).

---

### Post by diesch on 2009-10-03
You get that if the shell is expecting a final quote (" or ') or something like that.
Hit Ctrl-C to abort.

---

### Post by diesch on 2009-10-03
Ctrl-Z suspends the currently running program. To resume the suspended program type "fg"  at the prompt. Suspending doesn't help if the shell is just expecting some more input.

---

### Post by Alan Morgan on 2009-10-03
Thanks everyone.  That is exactly what I needed and more.  :P

A

---

### Post by fela on 2009-10-03
> **diesch said:**
> Ctrl-Z suspends the currently running program. To resume the suspended program type "fg"  at the prompt. Suspending doesn't help if the shell is just expecting some more input.

I didn't know that. Thanks for the knowledge, always welcome :)

---

