---
title: "Accidentally ran xkill on my desktop"
date: 2010-12-13
forum: General Help
---

### Post by eric1214 on 2010-12-13
So I created a shortcut for xkill and I entered it and clicked on my desktop. Now whenever I boot up Ubuntu, I just get a terminal prompt. No GUI at all. What should I do?  By the way, I'm running 10.10. Thanks!

---

### Post by jesseafrantz on 2010-12-13
> **eric1214 said:**
> So I created a shortcut for xkill and I entered it and clicked on my desktop. Now whenever I boot up Ubuntu, I just get a terminal prompt. No GUI at all. What should I do?  By the way, I'm running 10.10. Thanks!

did you try doing this:
```


Ubuntu:
/etc/init.d/gdm start

Kubuntu:
/etc/init.d/xdm start

```

---

