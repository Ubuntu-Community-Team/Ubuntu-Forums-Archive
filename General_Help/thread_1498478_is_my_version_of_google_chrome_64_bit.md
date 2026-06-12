---
title: "is my version of google chrome 64 bit?"
date: 2010-05-31
forum: General Help
---

### Post by xfearxnxloathing on 2010-05-31
how do i know if my version of google chrome is 64 bit or not?

i have 10.04 LTS 64bit installed and installed google chrome via google through firefox.

---

### Post by sdennie on 2010-05-31
If that's how you've installed it, try:

```

file /opt/google/chrome/chrome

```

That will tell you what type of binary it is.

---

### Post by xfearxnxloathing on 2010-05-31
> **sdennie said:**
> If that's how you've installed it, try:

```

file /opt/google/chrome/chrome

```

That will tell you what type of binary it is.

so_much_for_sleep@Ubu:~$ file /opt/google/chrome/chrome
/opt/google/chrome/chrome: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), stripped


looks like i'm good!  =]
thnx

---

