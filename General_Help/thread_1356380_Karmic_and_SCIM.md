---
title: "Karmic and SCIM"
date: 2009-12-16
forum: General Help
---

### Post by osarusan on 2009-12-16
Ever since upgrading to Karmic I've been having some issues using SCIM. In Jaunty, there was a nice SCIM bar in my panel which told me what langauge I was using. In Karmic, it's gone. However, I can still switch back and forth using ctrl-space, so that's not the main issue.

The main issue I'm having is that I have English and Japanese (only) installed, but occasionally, instead of Japanese, I'll get something that looks like Russian (or another cyrillic language). Since a few days ago, that's the only thing besides English I can get. I've checked my language settings, and only English and Japanese are marked as installed, but I can no longer type in Japanese.

How can I fix this??

---

### Post by Zorael on 2009-12-16
ibus (or I-Bus) is the new input method of choice in Ubuntu, so if you upgraded chances are it installed itself with a higher priority than SCIM. ibus still lacks some functionality that SCIM has, but SCIM is deadish upstream, so the change isn't entirely unwarranted. But even ibus should spawn a panel with which you can control what languages to input in.

The SCIM setup tool is still available by running **scim-setup** (Alt+F2). Likewise you can start ibus's setup with **ibus-setup**, though it won't start unless the ibus daemon itself is started.

---

### Post by osarusan on 2009-12-16
Ah great, that fixed it. I switched my language preferences over to ibus instead of scim and it appears to work now. Though I'm not getting anything in the panel...

Thanks for your help! :-)

---

