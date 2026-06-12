---
title: "C &amp; C++ Header Files?"
date: 2009-08-19
forum: General Help
---

### Post by Jetfire29 on 2009-08-19
I'm working on some programs that I brought over from a different linux machine, and am trying to compile and run them.  They compile just fine, but when I try to export them (ld -o sample sample.o, not sure what that's called), it gives me a bunch of errors about things that are not defined, like fscanf, fprintf, stdout, those things.  I installed build-essential, and g++, but neither one is working, so I'm assuming stdio.h is not found.  What can I do to get this file?

---

### Post by t4thfavor on 2009-08-19
Maybe post the errors, I think there are probably alot of errors that ld could throw, and I would probably be able to help better if I could see some errors.

---

### Post by Jetfire29 on 2009-08-19
here's what it puts out.
```
ld -o ATM ATM.o
ld: warning: cannot find entry symbol _start; defaulting to 00000000004000b0
ATM.o: In function `main':
ATM.c:(.text+0x62): undefined reference to `stdout'
ATM.c:(.text+0x76): undefined reference to `fwrite'
ATM.o: In function `get_pin':
ATM.c:(.text+0x90): undefined reference to `stdout'
ATM.c:(.text+0xa4): undefined reference to `fwrite'
ATM.c:(.text+0xab): undefined reference to `stdin'
ATM.c:(.text+0xbe): undefined reference to `fscanf'
ATM.c:(.text+0xd9): undefined reference to `stdout'
ATM.c:(.text+0xed): undefined reference to `fwrite'
ATM.o: In function `get_trans_num':
ATM.c:(.text+0x121): undefined reference to `stdout'
ATM.c:(.text+0x135): undefined reference to `fwrite'
ATM.c:(.text+0x13c): undefined reference to `stdin'
ATM.c:(.text+0x14f): undefined reference to `fscanf'
ATM.c:(.text+0x165): undefined reference to `stdout'
ATM.c:(.text+0x179): undefined reference to `fwrite'
ATM.c:(.text+0x18a): undefined reference to `stdout'
ATM.c:(.text+0x19e): undefined reference to `fwrite'
ATM.o: In function `get_acct_num':
ATM.c:(.text+0x1d2): undefined reference to `stdout'
ATM.c:(.text+0x1e6): undefined reference to `fwrite'
ATM.c:(.text+0x1ed): undefined reference to `stdin'
ATM.c:(.text+0x200): undefined reference to `fscanf'
ATM.c:(.text+0x216): undefined reference to `stdout'
ATM.c:(.text+0x22a): undefined reference to `fwrite'
ATM.o: In function `get_money_num':
ATM.c:(.text+0x254): undefined reference to `stdout'
ATM.c:(.text+0x268): undefined reference to `fwrite'
ATM.c:(.text+0x26f): undefined reference to `stdin'
ATM.c:(.text+0x282): undefined reference to `fscanf'

```

---

### Post by Jetfire29 on 2009-08-20
Can anyone help?  I really need to do this quick.

---

