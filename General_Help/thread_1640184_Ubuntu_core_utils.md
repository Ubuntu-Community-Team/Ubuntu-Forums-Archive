---
title: "Ubuntu core utils"
date: 2010-12-07
forum: General Help
---

### Post by ganga0 on 2010-12-07
Hi all. I am a c/c++ programmer and i've read some articles about linux kernel and gnu utils... And I decided to edit some core utils like ps, ls, top, etc. in my ubuntu.

So my questions is: what is the rightest way to get these packages' sources...

---

### Post by WorMzy on 2010-12-07
```
apt-get source coreutils
```


Should do it.

---

### Post by ganga0 on 2010-12-07
1. Yeah thx for answer, but i miss for example 'ps' util there.
2. Where can i get those sources now?

---

### Post by WorMzy on 2010-12-07
That's part of procps.

```
apt-get source procps
```

---

