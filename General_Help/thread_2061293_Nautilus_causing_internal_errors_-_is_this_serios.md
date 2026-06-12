---
title: "Nautilus causing internal errors - is this serios?"
date: 2012-09-22
forum: General Help
---

### Post by spaceshipguy on 2012-09-22
Nautilus just threw up its third internal error this week and I'm starting to wonder if I have a problem.

I was copying photos from one folder to another - big photos but not that big, a couple of MB each. But instead of copying the files over, the two Nautilus windows I had open went grey. Then an error message appeared telling me "Sorry, Ubuntu 12.04 has experienced an internal error."

I clicked to get details and it said;

nautilus crashed with SIGSEV in g_type_check_instance_cast()

and ...

Segfault happened at: 0x7fa4363a9dcc<g_type_check_instance_cast+28>: mov (%rax),%rbp PC(0x7fa4363a9dcc) ok
source "(%rax)" (0x746f685030322574) not located in a known VMA region (needed readable region)!
destination "%rbp" ok

Three of these in a week - each time with a lot of data though - feels a little unstable. Should I be worried?

Is there a fix?

---

