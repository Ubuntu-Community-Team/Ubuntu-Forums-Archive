---
title: "about the PS1 environment variable"
date: 2011-05-04
forum: General Help
---

### Post by wxuyec on 2011-05-04
I am using the konsole and the promotion is:
wxuyec@wxuyec-laptop:~$ 
can I change that to 1wxuyec@wxuyec-laptop:~$ 
by editing the PS1 environment variable, where 1
stands for the first tab.

thank you!

---

### Post by ~Plue on 2011-05-04
You can use an escaped lower case L (\l)

heres from the man page;
> \l               the basename of the shell's terminal device name

---

### Post by wxuyec on 2011-05-04
hi, thanks,

it works. but why does it count from 0 and next number is 2 not 1?
and what man page does your information come from?

many thanks.

---

### Post by ~Plue on 2011-05-04
> **wxuyec said:**
> 
it works. but why does it count from 0 and next number is 2 not 1?

Maybe a background process is using that pts device? Usually a re-login should reset it
> **wxuyec said:**
> 
and what man page does your information come from?

[man bash]("http://linux.die.net/man/1/bash")

---

### Post by wxuyec on 2011-05-04
thank you very much,
I will try is later.

---

