---
title: "linux-686 with pentium 4"
date: 2010-10-04
forum: General Help
---

### Post by Wakawakamush on 2010-10-04
hi,

i heard that the linux-686 kernel would work faster with my pentium 4 1.8 ghz. is that true? And what do i need to do to install it?

Wakawakamush

---

### Post by snowpine on 2010-10-04
Can you post the output of the following terminal command?

```
uname -m
```

---

### Post by Wakawakamush on 2010-10-04
Of course:


jorn@jorn-desktop:~$ uname -m
i686

does that 686 mean that i am already running linux-686 or that i need it?

---

### Post by snowpine on 2010-10-04
It means you are already running the correct kernel, which is no surprise, since Ubuntu has been extensively tested for years on Pentium 4's. :)

---

### Post by Wakawakamush on 2010-10-04
Ok, so i dont have to update my kernel to make ubuntu even faster?

---

### Post by snowpine on 2010-10-04
> **Wakawakamush said:**
> Ok, so i dont have to update my kernel to make ubuntu even faster?

Ubuntu has built-in support for the Pentium 4 (one of the most common processors in the world) without installing anything extra.

There are many ways to [make Ubuntu faster]("http://www.google.com/search?q=site:ubuntuforums.org+"make+ubuntu+faster""). But that is a separate topic.

---

### Post by bodhi.zazen on 2010-10-04
lubuntu 10.10 will run very fast on that processor.

In my experience, there are many reasons to run a custom kernel, increased speed is not one of them.

---

