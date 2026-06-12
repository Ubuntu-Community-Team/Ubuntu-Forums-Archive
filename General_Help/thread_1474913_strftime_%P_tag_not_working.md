---
title: "strftime %P tag not working"
date: 2010-05-06
forum: General Help
---

### Post by roberto.tomas on 2010-05-06
I'm playing with my bash prompt. got this nice pretty prompt with the hsitory number at the start, it looks like this:
```
[689] roberto@quad-g5: ~/Código/af9015 [01:24 ]$ 
```that space after the time is the \D{%P} tag -- it should read "am"/"pm" accourding to man 3 strftime
just to be sure the problem is with the underlying library, I tried date +%P -- it also reports nothing. date +%z reports my timezone correctly.. and my system clock is synched using NTP and is .. well, it's right.

any clue what is wrong here?


-- one other question I installed man pages in spanish since that's better for me.  manpages like "strftime" come up in spanish. But manpages like "date" still force me to read the english. What is going on there? Can I default to spanish?

---

### Post by roberto.tomas on 2010-05-29
I'd like to mark this as closed -- I've installed a bunch of things since then, and along the way the prompt started showing the "am" or "pm" for %p. The last thing I installed before noticing that this resolved was gnulib and lib6c-dev-ppc64, libc6-ppc64 to try to debug the problem :)

-- interesting to note that the libc6-ppc64 is **not** installed by default on a powerpc64-smp architecture.

---

### Post by dcstar on 2010-05-30
> **roberto.tomas said:**
> I'd like to mark this as closed
.

Then do it.

---

### Post by roberto.tomas on 2010-05-30
lol sounds like a plan :)

---

