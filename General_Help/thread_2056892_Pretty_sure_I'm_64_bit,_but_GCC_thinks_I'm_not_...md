---
title: "Pretty sure I'm 64 bit, but GCC thinks I'm not .."
date: 2012-09-12
forum: General Help
---

### Post by LeFou on 2012-09-12
Per
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

I have flags:
flags		: fpu vme de pse .. .[snip] lm ... 

meaning that my "processor is capable of 64-bit. "

But building Android source yields this, almost immediately:

"ERROR: prebuilts/tools/gcc-sdk/../../gcc/linux-x86/host/x86_64-linux-glibc2.7-4.6/bin/x86_64-linux-gcc only run on 64-bit linux"

Should I just head over to Android-land? Or is there a missing step between "capable of 64-bit" and "actually behaving like 64-bit" ?

---

### Post by Habitual on 2012-09-12
Do you have a 64 bit OS actually installed?

---

### Post by ragtag on 2012-09-12
Run
```
uname -p
```
in the terminal to check. It should say.
```
x86_64
```

---

### Post by LeFou on 2012-09-12
> **Habitual said:**
> Do you have a 64 bit OS actually installed?

I do not. That was the "missing step" :)
Can't remember why I chose 32 bit install.. was a long time ago.

---

### Post by Habitual on 2012-09-12
glad to be of help. :)

---

