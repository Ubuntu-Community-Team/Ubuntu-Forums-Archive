---
title: "stdlib no such file, need help"
date: 2010-04-03
forum: General Help
---

### Post by sumfarty1 on 2010-04-03
I am trying to compile a program and the compiler errors out saying 

stdlib.h no such file or directory

I have tried many things from the internet and nothing has worked

why cant my computer find the standard library?

---

### Post by sumfarty1 on 2010-04-03
it also cannot find avr/wdt.h

---

### Post by sumfarty1 on 2010-04-03
I have done the sudo apt-get install build-essential command
it did its stuff and it still doesn work

---

### Post by gmargo on 2010-04-03
If you installed the **build-essential** package, that also pulled in the **libc6-dev** package, which contains **/usr/include/stdlib.h**.

But you mention **avr/wdt.h**, so are you cross-compiling for an Atmel device?  If so you need the proper tools, not the standard build-essential host set.

---

