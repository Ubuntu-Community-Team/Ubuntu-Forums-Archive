---
title: "check what type of memory installed"
date: 2010-01-29
forum: General Help
---

### Post by spiky001 on 2010-01-29
Hi is there a way to check what type of memory is in a laptop & how much it can have,

---

### Post by llawwehttam on 2010-01-29
Try
```
free -m
```
in terminal. It will show you the total RAM in your system. Not sure how to check type except by opening it up.

---

### Post by lijcam on 2010-01-29
You could read the manual?

---

### Post by spiky001 on 2010-01-29
yea that is what i was after what type not how much it is using also how much memory MB can take

---

### Post by howefield on 2010-01-29
Try this command in a terminal (Applications > Accessories > Terminal)

```
sudo dmidecode -t17 |grep Size
```

It'll tell you what you have in each memory bank. If you have a spare blank for installing more memory, it'll also be obvious.

---

### Post by spiky001 on 2010-01-29
yea that worked told me what i had just need to know if there was anything to tell me what type eg, ddr and what speed it is just i ned to get some more memory just save me taking it apart 1st

---

### Post by howefield on 2010-01-29
Try this command.

```
sudo dmidecode
```

---

### Post by spiky001 on 2010-01-29
that done it ta

---

