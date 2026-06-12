---
title: "How can I put multiple windows inside the widget layer?"
date: 2010-12-11
forum: General Help
---

### Post by Mr_VeRiTy on 2010-12-11
Hi, I would like to put both Tomboy and Gwibber inside the widget layer, but so far I've only managed to add one or the other, I can add one by putting:
```
name=gwibber
``` into the "window match" box but how can I add another?

---

### Post by terobin on 2011-06-10
Put it all in brackets and separate each one with a | (Shift+\).
This might help you:
```
(name=tomboy | name=gwibber)
```

---

### Post by Mr_VeRiTy on 2011-06-10
> **terobin said:**
> Put it all in brackets and separate each one with a | (Shift+\).
This might help you:
```
(name=tomboy | name=gwibber)
```

I have already figured this out months ago (forgot to mark as solved...) but if anyone comes here trying to find out how to do this then at least they have the answer, thanks ^_^

---

