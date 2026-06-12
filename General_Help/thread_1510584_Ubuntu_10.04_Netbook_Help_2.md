---
title: "Ubuntu 10.04 Netbook Help 2"
date: 2010-06-15
forum: General Help
---

### Post by Mike808 on 2010-06-15
Well, here is another thing I would like to know.

I am using Ubuntu Netbook Edition 10.04 Session 2D.  How do I REMOVE the side categories thing.  I noticed at the top I can choose what I want.  How can I have it with just that and a NORMAL desktop?  Like icons, etc.

Or is that not possible with [B]Ubuntu 10.04 Netbook Edition?
[/B]

---

### Post by Mike808 on 2010-06-15
Bump.

---

### Post by fooman on 2010-06-15
try this:

go to system > preferences > startup applications

scroll through the list and uncheck "netbook launcher in EFL".

that should clear the netbook interface from the desktop.  next, if you see no icons on the screen,  then open a terminal and type:

```
gconf-editor
```

when it opens,  look on the left and go to: apps > nautilus > preferences.  then on the right,  put a check next to "show desktop".

that should get you the icons back.  hope that helps.

---

