---
title: "language support for japanese"
date: 2010-01-21
forum: General Help
---

### Post by snaggles on 2010-01-21
i'm quite new to the ubuntu community, so please bare with me. What I am trying to do is to be able to write in japanese in open office and firefox. I have already read several posts on how to set it up through scim, but I just can't get it to work. I've installed language support for japanese through administration>lanugage support. Scim is already installed but when I press <ctrl>+<space> nothing happens. I suspect that there's some incredibly simple solution to all of this, but I just can't get it to work!

---

### Post by tacutu on 2010-01-21
in a terminal type:
 ```
im-switch -c
```
and select scim-bridge. You might need to re-login before the changes take effect.

---

### Post by snaggles on 2010-01-21
Haha, oh my god! that was way too easy! Thank you so much. Worked like a charm :D

---

