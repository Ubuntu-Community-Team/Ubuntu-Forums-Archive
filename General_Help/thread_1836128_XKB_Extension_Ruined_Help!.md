---
title: "XKB Extension Ruined Help!"
date: 2011-08-30
forum: General Help
---

### Post by Jabrick on 2011-08-30
Hey so I was trying to get my windows key to become my meta key in emacs with the xkb extension, but I think I have made a mistake.
I did xkbcomp $DISPLAY
And edited the server file and compiled it.
But now alt and windows key not working at all.
Could someone please tell me how to get my default configuration back?
Thanks.
-From a panicked user.

---

### Post by notgary on 2011-08-30
I've no experience with the situation you describe, but it seems to me that the following page may help you out, 

[http://c2.com/cgi/wiki?RemapCapsLock](http://c2.com/cgi/wiki?RemapCapsLock)

specifically the first section that reads

> Unix, Console
If you have loadkeys (as you would under Linux), this should do the trick:
 loadkeys /usr/share/keymaps/i386/qwerty/emacs2.kmap.gz
To reset to the defaults (you may have to switch to another tty and back to undo ctrl-lock):
 loadkeys -d

---

### Post by Jabrick on 2011-08-31
Hey I have fxed it myself manually.
I guess its a good lesson to keep backups.
Thanks

---

### Post by Habitual on 2011-08-31
> **Jabrick said:**
> Hey I have fxed it myself manually.
I guess its a good lesson to keep backups.
Thanks

Amen to that!
+1 and props for doing so.

---

