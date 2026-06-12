---
title: "Undefined reference error _dl_stack_flags with gcc and pthreads"
date: 2011-04-21
forum: General Help
---

### Post by wadesworld on 2011-04-21
I am unable to compile a program that uses pthreads on Ubuntu 10.10 and gcc 4.4.  I also tried gcc 4.1.

It does not appear that going back to gcc 3.6 is an option that's available.

Full details at:

[http://stackoverflow.com/questions/5738000/undefined-reference-error-dl-stack-flags-with-gcc-and-pthreads]("http://stackoverflow.com/questions/5738000/undefined-reference-error-dl-stack-flags-with-gcc-and-pthreads")

Has anyone seen and solved this problem?

---

### Post by wadesworld on 2011-04-22
Just to update, this question has been answered.  The problem was that I was linking libpthread staticly, while libc was linked dynamically.  Changing to dynamic linking of libpthread solved the problem.

Full details can be found at:

[http://askubuntu.com/questions/36211/undefined-reference-error-dl-stack-flags-with-gcc-and-pthreads/36420#36420]("http://askubuntu.com/questions/36211/undefined-reference-error-dl-stack-flags-with-gcc-and-pthreads/36420#36420")

---

