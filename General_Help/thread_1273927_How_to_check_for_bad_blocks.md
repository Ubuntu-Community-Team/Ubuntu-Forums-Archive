---
title: "How to check for bad blocks"
date: 2009-09-23
forum: General Help
---

### Post by kehon on 2009-09-23
I want to check my laptop for bad blocks because I wan't to know the health of the hard drive. 

How can I do this when linux runs on the hard drive and I can't check while it's mounted?

Also how can I determine hard drive health based on the bad blocks?

---

### Post by QIII on 2009-09-24
You should be able to use badblocks from the LiveCD.

Before you do that 

```
man badblocks
```and read up to be sure what you are doing.

And remember -- if you find bad sectors it could be an indication of impending disk failure.

---

