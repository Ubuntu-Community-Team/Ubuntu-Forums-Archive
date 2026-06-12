---
title: "Ubuntu 11.10 Side bar/Dash missing"
date: 2011-11-14
forum: General Help
---

### Post by swo on 2011-11-14
Hi, I recently decided to try Ubuntu 11.10 and it's been going smooth. However my side bar disappeared and that makes things a bit off.  Before it went missing I was in CCSM, simply clicked one of the left navigation tabs and the whole computer seemed to lock up and freeze. I didn't get a chance to play with any settings, simply navigating to one of the left tabs seemed to cause a freeze. So after a few minutes I decided to restart my computer and that's when I noticed the side bar was gone. I've tried unity --reset and such in terminal and restarting after using it but no luck. Any idea's?

Edit, I found the problem. In case it helps someone else, ctrl+alt+t(terminal)
```
DISPLAY=:0.0 ccsm
```
Enable Unity Plugin. Don't know how that went off. Bye

---

### Post by hansdown on 2011-11-14
Welcome to the forum, swo.

Glad you fixed it.

---

