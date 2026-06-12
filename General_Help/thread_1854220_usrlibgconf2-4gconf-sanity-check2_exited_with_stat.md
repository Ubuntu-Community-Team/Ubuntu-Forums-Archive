---
title: "/usr/lib/gconf2-4/gconf-sanity-check2 exited with status 256"
date: 2011-10-03
forum: General Help
---

### Post by searchfgold6789 on 2011-10-03
Hi,
My mother's laptop is going through a brain fart of sorts right now... It's got this completely vexing problem where whenever I start it up, whether in failsafe graphics or just regular, I get an error after much screen-flickering saying:
```
/usr/lib/gconf2-4/gconf-sanity-check2 exited with status 256
```And it then takes me to a very plain login screen. When I try to log in, the same error occurs, always with an "OK" button.
Any help at all would be much appreciated with this issue!!!
 - search

---

### Post by searchfgold6789 on 2011-10-04
HUGE bump!

---

### Post by searchfgold6789 on 2011-10-05
Solved by running ```
sudo chmod 1777 /tmp
```
Metacity went loopy, so I just added a startup program called Metacity with the command `metacity --replace`.

---

