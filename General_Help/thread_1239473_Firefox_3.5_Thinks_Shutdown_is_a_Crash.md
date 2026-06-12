---
title: "Firefox 3.5 Thinks Shutdown is a Crash"
date: 2009-08-13
forum: General Help
---

### Post by JamieKitson on 2009-08-13
Hi,

after I shutdown my system (with halt, init 0) Firefox 3.5 restarts with:

Well, this is embarrassing. 
Shiretoko is having trouble recovering your windows and tabs. This is usually caused by a recently opened web page.

with the option to reopen my previous tabs. I would like it to do this automatically.

I have seen lots of reports of this, but all that I can see relate to 3.0. I had fixed it in 3.0 by setting:

browser.sessionstore.restore_prompt_uri = javascript:window.close();

but in 3.5 it's not a window. I am using dwm and jaunty.

Cheers, Jamie

---

