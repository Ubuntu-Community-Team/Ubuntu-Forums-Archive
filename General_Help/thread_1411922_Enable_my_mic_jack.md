---
title: "Enable my mic jack"
date: 2010-02-20
forum: General Help
---

### Post by RedSingularity on 2010-02-20
When i plug in my Mic the computer still wants to use the built in monitor mic.  How can i fix this problem?

---

### Post by RedSingularity on 2010-02-20
Nevermind, got it.  Adjusted some setting in alsamixer.

---

### Post by jpl888 on 2010-02-20
Run ```
alsamixer
``` from a terminal and look for bits that say "digital", fiddle with them. For instance my jack didn't work until I changed the first digital to "analog I".

See attached screen shot.

---

### Post by RedSingularity on 2010-02-20
Yeah it was exactly the same with mine.

---

