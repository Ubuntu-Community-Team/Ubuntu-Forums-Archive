---
title: "xchat blues"
date: 2006-06-13
forum: General Help
---

### Post by anubix on 2006-06-13
OK, so before today i've never had a problem with xchat... period!

but now, if say i'm in a large room  (no other rooms) and do an @find i get 5 private tabs, and the rest get scrambled together in the active window.  This makes actually tryin to understand them IMPOSSIBLE.  I've scoured the option menus, and /home/"usr"/.xchat2/xchat.conf for hours, and haven't made an iota of progress.

I have to fix this problem; is it a flood thing? (I've already re-installed twice)
If i can't get it to work, i'm going to be forced to wine mirc!
and i thought i was done with microsoft on my equipment....

---

### Post by DoomedTX on 2006-06-26
/set gui_auto_open_dialog ON [be sure there's no space after the ON or it will interpret it as OFF]

IIRC, this used to be a menu option that is no longer available in xchat2. If you search for "dialog" in the xchat config you should find the above setting at 0; change it to 1 for it to automatically come on. You may want to bind it to a key.

By the by, I found this answer to an old post of mine complaining about the flood protection on xchat.org:

> Try '/set *flood*'
All your flood settings are right there.

Good luck!

---

