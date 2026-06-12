---
title: "var/log/messages Interpretation &amp; format"
date: 2010-11-27
forum: General Help
---

### Post by Mecasickle on 2010-11-27
Hey guys im learning some RTAI and Kernel module programming.

When I load my hello World kerlenl module, most internet posts say that I should receive an output like this one, on the var/log/messages file :

Nov 27 19:50:40 user-laptop user: Hello World!

But I'm getting this:

Nov 27 19:50:40 user-laptop user:  [ 5892.922706] Hello World!

What does the : [ 5892.922706] mean???
Observation: I've noted that after every command logged, this number increases. It probably has to do with timing. But what's the exact interpretation? I'm interested in knowing what it means because I'm planning to work with a hard real-time system.

Any clues or ideas? Thanks guys!

Mecasickle

---

### Post by dcstar on 2010-11-27
> **Mecasickle said:**
> 
........
Nov 27 19:50:40 user-laptop user:  [ 5892.922706] Hello World!

What does the : [ 5892.922706] mean???
Observation: I've noted that after every command logged, this number increases. It probably has to do with timing. But what's the exact interpretation? I'm interested in knowing what it means because I'm planning to work with a hard real-time system.

Any clues or ideas? Thanks guys!

Mecasickle

Seconds since kernel start (boot up).

---

