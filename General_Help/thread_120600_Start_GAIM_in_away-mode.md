---
title: "Start GAIM in away-mode"
date: 2006-01-22
forum: General Help
---

### Post by breakman on 2006-01-22
How du start up gaim in away-mode?
I've tryed "gaim -w" and "gaim --away" with no success...

---

### Post by d1337 on 2006-01-22
man gaim displays this bit of info
 ```
-w, --away[=MESG]
              Automatically  go  away  on  signon.  You may optionally use the
              MESG parameter to set the away message.
```
which you may have already known.  I'd assume, though, that you may need to configure it with [=MESG] to have it work properly.  I'll keep picking for a few minutes.

d1337

edit- No, it appears as if MESG is completely optional.  I'll keep looking

---

### Post by xerosis on 2006-01-23
the beta version of gaim signs you on using your last used status.

---

