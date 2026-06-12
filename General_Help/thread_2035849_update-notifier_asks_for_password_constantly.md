---
title: "update-notifier asks for password constantly"
date: 2012-07-31
forum: General Help
---

### Post by errrn on 2012-07-31
Hi,

I've been getting a lot of "report this crash"-type messages, but not the usual ones. I'm asked for my password.

It's not apport prompting me to report a crash and go on, but something else.

After googling around a bit, with **this**(*****) command I (think I) identified the process doing this

*** **```

xprop _NET_WM_PID | sed 's/_NET_WM_PID(CARDINAL) = //' | ps `cat`
```I reinstalled it, but it keeps doing the same thing. killing the process helps, of course, but I'd like to know what's really going on.

any ideas?
thx

EDIT: running 12.04 on i3, 4GB, and ati video.

---

