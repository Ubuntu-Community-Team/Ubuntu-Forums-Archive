---
title: "make commands run on terminal start-up"
date: 2010-07-01
forum: General Help
---

### Post by goseph on 2010-07-01
Hi all!

I added this:

```

clear
fortune | cowsay | echo

```

to the bottom of my .profile expecting a cow to tell me a fun quote whenever i pull up a terminal. It hasn't done anything, however. How do I achieve my desired effect?

---

### Post by jwbrase on 2010-07-01
Leave off the pipe to echo at the end.

fortune | cowsay does what you want, trying to pipe it to echo throws it away.

---

### Post by yetiman64 on 2010-07-01
It won't work at all if you put it in ~/.profile (tested the commands below here and it does nothing). Put the commands below (as described by jwbrase) at the end of your ~/**.bashrc file**. The commands being

```
clear
fortune | cowsay
``` As explained in the last post by jwbrase, drop the 2nd pipe symbol and the echo command.

I now have a "talking cow" in my terminal every time I open it, doing it this way :).

---

### Post by goseph on 2010-07-03
Thanks a lot guys! I am enjoying the cow goodness now,

I stumbled upon this alternate script to randomize the animals if this is of interest to anybody..


[http://www.doknowevil.net/2010/02/03/random-cowish-animals-preaching-quotes-on-ubuntu-910/](http://www.doknowevil.net/2010/02/03/random-cowish-animals-preaching-quotes-on-ubuntu-910/)

---

### Post by yetiman64 on 2010-07-03
> **goseph said:**
> ...I stumbled upon this alternate script to randomize the animals if this is of interest to anybody..

That is one brilliant script; some of the art is absolutely phenomenal (love the dragon one). Thanks for the link goseph.

---

