---
title: "Unknown key"
date: 2006-03-23
forum: General Help
---

### Post by thumper on 2006-03-23
I get this a lot in /var/log/messages (about 1000 times in the current file):
```
Mar 23 13:29:56 localhost kernel: [4889931.302000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Mar 23 13:29:56 localhost kernel: [4889931.302000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.

```

I don't seem to be using anything strange... at least I don't think so.

Ideas anyone?

---

### Post by SeanTater on 2006-03-23
Check if a key in your keyboard is stuck. Especially a non-standard one like "e-mail"..

---

### Post by thumper on 2006-03-23
Hmm... a bit of trial an error and it appears to be the arrow keys.

I had one konsole open with "tail -f /var/log/messages" and another konsole open where I started pressing keys - starting with the "special" ones (even though it is the oldest natural keyboard there is).

Up arrow generates the message twice and also shows the history in the konsole, so not entirely sure what is happening there...

---

### Post by dentament on 2006-06-15
See this:
[http://www.ubuntuforums.org/showthread.php?t=76271&highlight=atkbd.c](http://www.ubuntuforums.org/showthread.php?t=76271&highlight=atkbd.c)

---

