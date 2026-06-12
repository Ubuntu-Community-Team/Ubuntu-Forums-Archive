---
title: "System locale changed to Chinese?"
date: 2012-07-10
forum: General Help
---

### Post by dewdrop_world on 2012-07-10
Here's what I did:

Installed mail-notification (synaptic)
Ran the mail-notification configuration tool from the Internet menu.
No icon in the panel.
So I thought, maybe a restart will get it going.
Log in: Ubuntu says "You are logging in with a new language."

locale -->
LANG=zh_CN.UTF-8
LANGUAGE=zh_CN:en
LC_CTYPE="zh_CN.UTF-8"
LC_NUMERIC=en_US.UTF-8
LC_TIME=en_US.UTF-8
LC_COLLATE="zh_CN.UTF-8"
LC_MONETARY=en_US.UTF-8
LC_MESSAGES="zh_CN.UTF-8"
LC_PAPER=en_US.UTF-8
LC_NAME=en_US.UTF-8
LC_ADDRESS=en_US.UTF-8
LC_TELEPHONE=en_US.UTF-8
LC_MEASUREMENT=en_US.UTF-8
LC_IDENTIFICATION=en_US.UTF-8
LC_ALL=

Ummmmm... why? I did no such thing.

I'll change it back using "locale" but this is really bizarre. I haven't a clue why it would do that.

Any ideas?

---

