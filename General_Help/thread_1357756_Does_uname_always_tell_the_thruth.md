---
title: "Does uname always tell the thruth?"
date: 2009-12-17
forum: General Help
---

### Post by Fixman on 2009-12-17
I am currently in a 32-bit version of Ubuntu, however I don't know if my processor is 32-bit or 64-bit. Uname reports my processor as **i686**. Is that my real processor, or the one Ubuntu "thinks" I have?

---

### Post by adaucourt on 2009-12-17
> **Fixman said:**
> I am currently in a 32-bit version of Ubuntu, however I don't know if my processor is 32-bit or 64-bit. Uname reports my processor as **i686**. Is that my real processor, or the one Ubuntu "thinks" I have?

do this:
```
dmesg | grep CPU
```

---

### Post by SlugSlug on 2009-12-17
whats the output of
```
cat /proc/cpuinfo 
```

if it contains 'lm'  in the flags -- it's 64bit

---

### Post by Fixman on 2009-12-17
> **SlugSlug said:**
> whats the output of
```
cat /proc/cpuinfo 
```

if it contains 'lm'  in the flags -- it's 64bit

Great, so my Laptop has a 64-bit processor. However, can someone then help me in <a href=http://ubuntuforums.org/showthread.php?t=1357109>this</a> problem? I really don't have a single clue now.

---

### Post by dcstar on 2009-12-17
> **Fixman said:**
> Great, so my Laptop has a 64-bit processor. However, can someone then help me in <a href=http://ubuntuforums.org/showthread.php?t=1357109>this</a> problem? I really don't have a single clue now.

How about following some of the advice in that thread?

---

### Post by bodhi.zazen on 2009-12-17
> **Fixman said:**
> I am currently in a 32-bit version of Ubuntu, however I don't know if my processor is 32-bit or 64-bit. Uname reports my processor as **i686**. Is that my real processor, or the one Ubuntu "thinks" I have?

uname does not report your CPU arch, I believe it reports the arch flag used to compile your kernel.

---

