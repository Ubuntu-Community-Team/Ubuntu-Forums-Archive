---
title: "Issue When Installing PCEmu"
date: 2009-08-20
forum: General Help
---

### Post by nathanpc on 2009-08-20
[LEFT]Hello,
 I'm learning Assembly, but i'm already a Java and C++ developer, but when i run a make in the path o [PCEmu]("http://pcemu.sourceforge.net/") to install it gave me an error, here is the console log:
```
eeepc@eeepc:~/Desktop/pcemu$ make
gcc -Wall -O2 -fomit-frame-pointer -fno-strength-reduce -DALIGNED_ACCESS -DBIGCASE -DINLINE_FUNCTIONS -DDISABLE_MFS -c cpu.c
In file included from cpu.c:26:
cpu.h:125:2: error: #error 
cpu.c:1747:1: error: pasting "i_jo" and "(" does not give a valid preprocessing token
cpu.c:1748:1: error: pasting "i_jno" and "(" does not give a valid preprocessing token
cpu.c:1749:1: error: pasting "i_jb" and "(" does not give a valid preprocessing token
cpu.c:1750:1: error: pasting "i_jnb" and "(" does not give a valid preprocessing token
cpu.c:1751:1: error: pasting "i_jz" and "(" does not give a valid preprocessing token
cpu.c:1752:1: error: pasting "i_jnz" and "(" does not give a valid preprocessing token
cpu.c:1753:1: error: pasting "i_jbe" and "(" does not give a valid preprocessing token
cpu.c:1754:1: error: pasting "i_jnbe" and "(" does not give a valid preprocessing token
cpu.c:1755:1: error: pasting "i_js" and "(" does not give a valid preprocessing token
cpu.c:1756:1: error: pasting "i_jns" and "(" does not give a valid preprocessing token
cpu.c:1757:1: error: pasting "i_jp" and "(" does not give a valid preprocessing token
cpu.c:1758:1: error: pasting "i_jnp" and "(" does not give a valid preprocessing token
cpu.c:1759:1: error: pasting "i_jl" and "(" does not give a valid preprocessing token
cpu.c:1760:1: error: pasting "i_jnl" and "(" does not give a valid preprocessing token
cpu.c:1761:1: error: pasting "i_jle" and "(" does not give a valid preprocessing token
cpu.c:1762:1: error: pasting "i_jnle" and "(" does not give a valid preprocessing token
make: *** [cpu.o] Error 1
```Remember that i'm using the version 1.2
Thanks,
 Nathan Paulino Campos
[/LEFT]

---

### Post by uarale on 2009-09-14
Can anyone help on this? I'm facing the same problem.

---

