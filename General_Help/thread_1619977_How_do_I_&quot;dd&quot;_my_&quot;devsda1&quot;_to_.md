---
title: "How do I &quot;dd&quot; my &quot;/dev/sda1&quot; to all zero's?"
date: 2010-11-12
forum: General Help
---

### Post by unone95 on 2010-11-12
How do I use dd to make my /dev/sda1 partition all zeros?

/dev/sda1 Is unformated. and /dev/sda2 is formated and has data. Already backed up the hard drive if this attempt goes bad.

Please give me a detailed example as I am an absolute beginner. Again, I want to stress that I am new to all this bash stuff, please go easy on me.

Oh and if there is gui version lmk lol

---

### Post by lmarmisa on 2010-11-12
Open a terminal and type:

```

sudo dd if=/dev/zero of=/dev/sda1

```

---

### Post by unone95 on 2010-11-12
Thanks that was painless. :P:P

---

### Post by alphaamanitin on 2010-11-12
Just wanted to point out that command supplied will take a long time to zero out a drive.  Adding bs=16M or bs=32M will make the process go much faster.

AlphaA

---

### Post by unone95 on 2010-11-13
Next question,

What if you wanted to use a patten like 01010101 etc or some other algorithm?

---

### Post by dcstar on 2010-11-14
> **unone95 said:**
> **Next question**,
.......

**No**, you have your answer for this thread, mark it solved and ask a new question.

---

