---
title: "Crash on login from lightdm (Ubuntu 12.04)"
date: 2012-10-11
forum: General Help
---

### Post by kw217 on 2012-10-11
Finally managed to figure out why I couldn't log into my account from the greeter, but all the other users could. Every time I logged in it went to the text console for half a second or so, then straight back to the greeter again. No interesting logs anywhere: not /var/log/Xorg.0.log, not ~/.xsession-errors, not anything else in /var/log, /var/log/lightdm, or /var/crash. It just looked like I went into the X session then immediately exited, with no errors.

Solution: my ~/.Xauthority file was owned by root:root and chmod'd r---------. Oops! I deleted it (via sudo) along with two other .Xauthority* files, and voila, it all works now!

Posting here in case anyone else has the same problem.

--KW 8-)

---

