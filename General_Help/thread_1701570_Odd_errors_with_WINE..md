---
title: "Odd errors with WINE."
date: 2011-03-06
forum: General Help
---

### Post by trappingnoobs on 2011-03-06
I'm using wine 3.(I think 0.15) and booting IE 7 just repeatedly brings up the install screen. I can boot it from inside the Program files directory, but that one can't open any websites.

I'm also having trouble installing a game called Roblox, which brings up the updating bar, then closes the update window and does nothing past that point, and others have reported theirs worked.

I've tried 2.(12?), which is their stable release; same thing, I've also tried reinstalling both wine and IE7.

Anyone know what's going on?

---

### Post by LoneWolfJack on 2011-03-06
check your programs against appdb. IE7 is listed as "garbage", so you won't get it to run with wine.

[http://appdb.winehq.org]("http://appdb.winehq.org")

use a VM instead.

---

### Post by davidmohammed on 2011-03-06
use winetricks to install ie7 - dont try to install it yourself.

- from the terminal, type 

```
winetricks
```

---

