---
title: "restart doesn''t work in 10.4"
date: 2010-05-05
forum: General Help
---

### Post by Andy Norfolk on 2010-05-05
In Ubuntu 10.4 the restart option behaves like log off. It doesn't restart my computer just takes me to a log in screen.

Any suggestions?

---

### Post by Andy Norfolk on 2010-05-05
Well after the latest updates it now works correctly - how odd!

---

### Post by Andy Norfolk on 2010-05-08
And now I'm back to having the same problem. 

If I try to restart or turn off my computer I end up back at the log in screen. The button bottom right of the log in screen with the restart or quit options does nothing.

Doh!

---

### Post by virtualXTC on 2012-01-26
Same issue here, but I'm using oneiric (11.10).

---

### Post by virtualXTC on 2012-01-26
Turns out this was an instance of me shooting myself in the foot:  the g/f shut down the machine while I had a recording scheduled, so I took away the ability for any non-root user to shut down the system, thus none of the gui commands work.

to verify you are having the same problem, open a terminal and type:
reboot

if you get the error:
reboot: Need to be root

then you need to grant your users permission to shut down the systemusers

---

### Post by virtualXTC on 2012-01-26
tuns out I shot my self in the foot:  the g/f shutdown once while I had a scheduled recording several months ago.  In a sleep deprived state I apparently changed the user permissions so that only rroot users could shut down.  Typeing the reboot command from a terminal confirmed this.

---

