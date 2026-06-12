---
title: "Customize my KDE session"
date: 2006-05-04
forum: General Help
---

### Post by albox on 2006-05-04
Hi,
I'd like to customize my KDE session launched remotely. I use the following commands :
ssh -X host
startkde

For example, is it possible to launch several consoles after login. I'd like to use different settings for each console.
I'm also interested in using the same style (theme, walpapper,...) every time I use X to start a KDE session.
Can you help me ?
Thank you :D

---

### Post by louis_nichols on 2006-05-04
Well... I don't see why kde via ssh would behave any differently than the normal kde, for the same user. So...

For the second issue: open the kde control center, go to KDE components>Session manager and check "restore previous session"

As for the first, I'm not sure I understant what you need, but konsole does have the possibility to configure profiles: different look, different behavior...

---

### Post by albox on 2006-05-05
That's strange because every time I launch KDE on a different hostname, I also have a different style. Maybe because, it's not the same version ?
Where are stored the parameters used ?

---

