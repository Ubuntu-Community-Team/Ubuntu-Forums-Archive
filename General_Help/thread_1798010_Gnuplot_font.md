---
title: "Gnuplot font"
date: 2011-07-05
forum: General Help
---

### Post by Paradigm6790 on 2011-07-05
Hello all,

I have a rather complicated gnuplot set up that worked perfectly until I ported it over on our linux server. Now I have everything running except that it doesn't seem to support enhanced fonts.

by not accepting these fonts, it pushes everything else out of alignment and the tics are small enough that I *need* smaller text.

My question is this:

Is there any way to make text smaller in gnuplot without the use of enhanced fonts?

Thanks in advance!

---

### Post by Bachstelze on 2011-07-05
What was the platform where it worked? If the "enhanced fonts" thing is a compile-time option that is not enabled in the Ubuntu package, it might be easier to recompile it with that option enabled than changing your plot script.

---

### Post by Paradigm6790 on 2011-07-06
I don't think it ever compiles. A gnuplot script is basically a test file of commands and I run gnuplot on the linux side calling that text file and it interprets it.

I was using windows when it was working.

---

