---
title: "Switching from intel syntax to AT&amp;T Assembly Language"
date: 2012-07-30
forum: General Help
---

### Post by FerasMoalla on 2012-07-30
Hi

Sorry about the misleading heading. I am using Ubuntu 10.04, currently using the GDB to disassemble programs, however the assembly language syntax is configured to AT&T and I need to switch to Intel syntax, in the older versions of Ubuntu I could simply type:

gdb -q
(gdb) set dis intel

Then its set, or I could type:

echo "set dis intel" > ~/.gdbinit 

This is obviously not working in my current version, any idea how to do that?

Thanks

---

