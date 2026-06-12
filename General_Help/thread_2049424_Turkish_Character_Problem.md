---
title: "Turkish Character Problem"
date: 2012-08-28
forum: General Help
---

### Post by HasanOzbey on 2012-08-28
I set my keyboard as "Turkish Q", but i still can't write turkish characters. 

Interesting point: I'm changing a random option from "System Settings -> Keyboard -> Turkish Q -> Options..." and turning it back, however, i can write turkish characters well. But the problem is coming back when i restart my computer.

Any solutions?

---

### Post by HasanOzbey on 2012-08-31
UP!
Output for `locale`:
```

LANG=tr_TR.UTF-8
LANGUAGE=
LC_CTYPE="tr_TR.UTF-8"
LC_NUMERIC="tr_TR.UTF-8"
LC_TIME="tr_TR.UTF-8"
LC_COLLATE="tr_TR.UTF-8"
LC_MONETARY="tr_TR.UTF-8"
LC_MESSAGES="tr_TR.UTF-8"
LC_PAPER="tr_TR.UTF-8"
LC_NAME="tr_TR.UTF-8"
LC_ADDRESS="tr_TR.UTF-8"
LC_TELEPHONE="tr_TR.UTF-8"
LC_MEASUREMENT="tr_TR.UTF-8"
LC_IDENTIFICATION="tr_TR.UTF-8"
LC_ALL=

```

*Note: **sudo setxkbmap tr** is a temporary fix. (Trouble is coming back after restart)*

---

