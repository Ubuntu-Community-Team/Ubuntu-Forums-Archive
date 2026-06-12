---
title: "Unable to remove pidgin shortcut from the indicator applet"
date: 2010-10-21
forum: General Help
---

### Post by jurij89 on 2010-10-21
Hi!
I installed pidgin a while ago, and after using it I decided to stick with empathy...
when I installed it, a shortcut to it appeared in the Indicator applet
now, that I have uninstalled it, the shortcut remains although clicking on it doesn't do anything...
does anybody know a simple way of removing the shortcut from the indicator applet?
thanks!

---

### Post by pz.daniel on 2011-01-15
hello jurij89,

i just had the same problem and was looking for a solution.
here's what i did:

open a terminal (ctrl+alt+t) and do

sudo rm /usr/share/indicators/messages/applications/pidgin

that's it!

hope it helps and you still need it ;-)

oh, by the way. you can also remove any other program listet in the indicator-applet with that method.


best regards
daniel

---

