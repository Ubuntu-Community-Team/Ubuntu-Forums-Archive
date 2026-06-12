---
title: "Firefox starts but grays out"
date: 2010-09-13
forum: General Help
---

### Post by charonred on 2010-09-13
When Firefox starts, it loads the home page (Google), but then it greys out and ceases operating - even the '**Well , this is embarrassing**' page when it restarts after a forced close greys out. I've used Synaptic to re-install Firefox, but it makes no difference. 

At the moment I can't use Firefox as my main browser (which has all my most recent bookmarks/passwords etc in it), I'm using Google Chrome to post this.

Anybody got an idea how to fix Firefox?

---

### Post by hrickh on 2010-09-13
> **charonred said:**
> Firefox has suddenly begun starting, but as soon as it loads the home page (Google), it greys out - even the '**Well , this is embarrassing**' page when it restarts after a forced close greys out. I've used Synaptic to re-install Firefox, but it makes no difference. 

At the moment I can't use Firefox as my main browser (which has all my most recent bookmarks/passwords etc in it), I'm using Google Chrome to post this.

Anybody got an idea how to fix Firefox?
Recently install a plugin/addon?

I've had this happen with pad plugins. If you absolutely can't get past the gray-out, you can always wipe your profile (delete it). It's located in ~/.mozilla/

There's also a subdirectory in there called bookmarkbackups. You maw want to save that to salvage your bookmarks.

R.
==

---

### Post by Grenage on 2010-09-13
Run:

```
firefox -safe-mode
```

Try disabling all add-ons, then loading it normally.  If it works, enable them one at a time.

---

### Post by charonred on 2010-09-13
thanks, I started in safe-mode and disabled 'Bindwood' don't know where that came from (I don't recall adding it) - seems to be working ok, so I'll get my start-page tabs setup again.

---

### Post by Grenage on 2010-09-13
It looks like it might be an UbuntuOne add-on, so you probably didn't add it manually.

---

### Post by hrickh on 2010-09-13
> **Grenage said:**
> It looks like it might be an UbuntuOne add-on, so you probably didn't add it manually.
Yeah, it's part of UbuntuOne's bookmark sync feature.

Personally, I'm not a fan of UbuntuOne... too many problems reported.

charonred, if you want to sync your bookmarks, I'd recommend something more along the lines of xmarks.

R.
==

---

