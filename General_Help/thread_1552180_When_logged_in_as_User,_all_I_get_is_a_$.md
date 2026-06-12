---
title: "When logged in as User, all I get is a $"
date: 2010-08-13
forum: General Help
---

### Post by CrusaderAD on 2010-08-13
I'm getting some weird behavior when I log in via ssh to a ubuntu server. When I log in, there is only a $ at the command prompt, no user name. The arrows don't work, they just put the arrow characters in the prompt. Everything else seems to be ok. Any ideas?

**Also, when I say logged in as User, I meant a new user I just created.

---

### Post by Noz3001 on 2010-08-13
Have you set the shell to /bin/bash? Look's like you're in /bin/sh

---

### Post by CrusaderAD on 2010-08-13
> **Noz3001 said:**
> Have you set the shell to /bin/bash? Look's like you're in /bin/sh

Yep, that was it. Thanks!

---

