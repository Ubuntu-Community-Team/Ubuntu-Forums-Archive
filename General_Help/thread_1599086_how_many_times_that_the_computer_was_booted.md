---
title: "how many times that the computer was booted?"
date: 2010-10-17
forum: General Help
---

### Post by mhmtyavuz on 2010-10-17
Hi there. I'm a Computer engineering student. I'm using ubuntu 10.04 I would like to ask something about my homework. where can I get info about how many times did my computer was booted?

the question in homework is like this:
"Write a shell script which includes a single argument which is a number.
Then, it will show the number of times that the computer was booted during last “number” of days
(including today).
**Hint: This information is recorded somewhere in your system**."

where is it recorded?

Thanks for help...

---

### Post by mhmtyavuz on 2010-10-17
please anyone help? I googled it but found nothing

---

### Post by VMC on 2010-10-17
You might want to try the 'last' command, but if you have removed "/var/log/wtmp" your out of luck. 'man last' will explain options to use.

---

