---
title: "How does one disable colour highlighting in vi"
date: 2010-05-14
forum: General Help
---

### Post by dantalion23 on 2010-05-14
I wish to disable the colour highlighting in the vi text editor. I tried creating an empty .gvimrc file in my home directory but this had no effect. Can anyone point me in the right direction?

---

### Post by anglican on 2010-05-14
> **dantalion23 said:**
> I wish to disable the colour highlighting in the vi text editor. I tried creating an empty .gvimrc file in my home directory but this had no effect. Can anyone point me in the right direction?
In an individual session you can type:

```
:syntax off
```Or you can put that (without the colon, obviously) into your .gvimrc file.

H

---

### Post by dantalion23 on 2010-05-17
Thank you Anglican. The colours were driving me insane, everything in my life is now monochrome.

---

