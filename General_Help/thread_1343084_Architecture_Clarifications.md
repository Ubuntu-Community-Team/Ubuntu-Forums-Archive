---
title: "Architecture Clarifications?"
date: 2009-12-01
forum: General Help
---

### Post by thomasjones on 2009-12-01
Hello all,

I am currently developing software that lists ALL packages available for the plethora of ubuntu variants and architectures. Problem is that I want to ensure that my approach is entirely correct.

This is what I need clarified:

1 - All OFFICIALLY released packages are available for each supported architecture? For instance the "gawk" package-----is it available in i386, amd64, hppa, ia64 and powerpc architectures?

2 - My architecture on this machine is i686; determined via uname -m. What is the OFFICIAL representation regarding the package architecture? Is it x86, i386 or i686?

I queried dpkg for "gawk" and it states verbatim "Architecture: i386". So there seems to be a discrepancy.

Cheers.
Thomas

---

