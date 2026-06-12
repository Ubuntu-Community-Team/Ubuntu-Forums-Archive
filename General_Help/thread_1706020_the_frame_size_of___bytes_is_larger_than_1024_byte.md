---
title: "the frame size of *  bytes is larger than 1024 bytes"
date: 2011-03-13
forum: General Help
---

### Post by ufuser01 on 2011-03-13
Hi,

This probably is a GCC question (Ver 4.4), but I have seen this discussed here many times: 

**Problem:**
I moved from Ubuntu 8.04 to 10.04 and working on some code and I saw this message for one of my functions (multiple times for the same function)

**the frame size of *  bytes is larger than 1024 bytes**

What I learnt is that this is a warning, that was set under "Kernel Hacking Menu".  However, this version of Ubuntu, is from a LIve CD and it is set to 1024. 

**My questions:**
1. Is there anyway other than recompiling the kernel, to get rid of this warning?
2. What are the consequences of ignoring this warning, and why does it matter anyway? I don't understand the "frame size". 

Thanks.

---

### Post by treblih on 2011-08-01
check here
[http://stackoverflow.com/questions/2450845/what-does-this-error-mean-somefile-c200-error-the-frame-size-of-1032-bytes-i](http://stackoverflow.com/questions/2450845/what-does-this-error-mean-somefile-c200-error-the-frame-size-of-1032-bytes-i)

u've allocate a local var which is larger than 1024 :)

---

