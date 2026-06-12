---
title: "Guide to learn C"
date: 2009-11-29
forum: General Help
---

### Post by ubudog on 2009-11-29
Hi, does anyone know of a good guide to learn C programming?

---

### Post by Alex Libman on 2009-11-29
There are some nice public domain books / tutorials like *[Learning GNU C]("http://www.nongnu.org/c-prog-book/online/index.html") *and [others]("http://www.freeprogrammingresources.com/ctutor.html"), and one can find even nicer ones scanned in as PDF's if one knows how to search P2P.  ;)

C is a language that is much harder to master than it is to learn: you need to have a good understanding of computer science fundamentals, common pitfalls of software engineering, memory management, debugging, the mesh of available libraries you can use (which very often overlap in functionality), and so on.  Becoming a good C programmer also requires A LOT of reading of other people's code to learn from their experience.

C is definitely a language every experienced programmer should know (as opposed to C++, C#, Java, Pascal, VB, any of them snooty academic functional languages, etc), because pretty much every serious OS kernel and system core is written in C, but it isn't good as an all-purpose language for every job out there.  The ideal is to split your programming into [two paradigms]("http://en.wikipedia.org/wiki/Ousterhout%27s_dichotomy"): C for systems programming and inner loops, and a lightweight scripting language like Perl, PHP, Tcl, [JavaScript]("http://code.google.com/p/v8/"), etc for everything else.  I most often start coding in Python or Lua, and then re-write some modules in C if (and only if) further optimization is desirable (or if the high-level scripting language libraries are missing some features I need, which doesn't happen very often).

---

