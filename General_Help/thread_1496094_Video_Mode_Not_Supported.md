---
title: "Video Mode Not Supported"
date: 2010-05-28
forum: General Help
---

### Post by DaftPyramid on 2010-05-28
Tried to install the ATI proprietary drivers (fglrx), but when I boot up, all I get is "Video Mode Not Supported". I suspect my refresh rate or resolution is the problem, but I don't know how to change it from the terminal (ctrl-alt-f1)

Any help?

---

### Post by DaftPyramid on 2010-05-28
Please Help.

---

### Post by DaftPyramid on 2010-05-28
Please.

---

### Post by DaftPyramid on 2010-05-28
For God's sake, can someone at least say *something* so I know that I'm not just talking to myself here?

---

### Post by DaftPyramid on 2010-05-29
Anything, anything at all. This is messing with my sanity.

---

### Post by clhsharky on 2010-05-29
DaftPyramid

It would help if we knew what video chip you have.

```
lspci
```

sharky

---

### Post by DaftPyramid on 2010-05-29
It's an integrated ATI Radeon Xpress 200. 

Apparently, the card isn't supported by fglrx anymore, but on AMD's website, choosing my card brings you to the Catalyst fglrx download page. Considering the free Radeon drivers don't work properly, I figured I'd try it.

---

### Post by DaftPyramid on 2010-05-29
lspci | grep VGA yields...

ATI Technologies Inc RS480 [Radeon Xpress 200G Series]

---

### Post by lisati on 2010-05-29
> **DaftPyramid said:**
> Please Help.

> **DaftPyramid said:**
> Please.

> **DaftPyramid said:**
> For God's sake, can someone at least say *something* so I know that I'm not just talking to myself here?

> **DaftPyramid said:**
> Anything, anything at all. This is messing with my sanity.
Please be patient, we're all volunteers here. The usual expectation is that you try to wait 24 hours before bumping your thread.

---

### Post by DaftPyramid on 2010-05-29
Yes, I apologize. I was frustrated and impatient. 

In any case, I've reverted to the free Radeon drivers, which unleashes an entirely new set of problems. This thread may be locked.

---

