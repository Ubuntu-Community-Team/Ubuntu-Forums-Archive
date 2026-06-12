---
title: "32bit vs 64 bit ubuntu which...."
date: 2010-10-27
forum: General Help
---

### Post by choochoousmc on 2010-10-27
how do I tell which one do I have, or are there two.
thanks

---

### Post by baddnady23 on 2010-10-27
try ```
uname -m
```

---

### Post by Verbeck on 2010-10-27
> **choochoousmc said:**
> how do I tell which one do I have, or are there two.
thanks

EDIT: better way , as posted below by [gradysghost]("http://ubuntuforums.org/member.php?u=563645")

type in the terminal 
```
uname -m
```it should output something like 

i686 means that its the 32bit version. if its 64bit then it will say x86_64

---

### Post by gradysghost on 2010-10-27
Launch a terminal.  Run this:

```
uname -m
```

This will list something like:

```
i686
```

...which suggests that you are using the x86 (32-bit) version of Ubuntu.

---

### Post by gradysghost on 2010-10-27
Verbeck beat me by seconds!  Drat!

---

### Post by Verbeck on 2010-10-27
> **gradysghost said:**
> verbeck beat me by seconds!  Drat!
:p

and baddnady23 beat me by seconds

---

### Post by linux-hack on 2010-10-27
i686 = 32bits
x86_64 = 64bits

---

