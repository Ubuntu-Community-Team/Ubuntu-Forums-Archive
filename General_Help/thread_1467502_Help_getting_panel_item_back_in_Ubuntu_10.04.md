---
title: "Help getting panel item back in Ubuntu 10.04"
date: 2010-04-30
forum: General Help
---

### Post by Durandal512 on 2010-04-30
I'm an idiot.  I upgraded to 10.04 and took care of the problem with compiz that arose.  Everything went fine.  Then, for some reason I'm not quite sure of, I ended up right-clicking on the little menu item in the top right hand corner of the screen.  I went to click out of the right-click menu, and I accidentally hit "Remove from panel".  I have attached a picture of where the item in question was.  Can someone help me out with this?

EDIT:  I also should mention that I have looked in the menu of panel items (right-click on panel, Add to Panel), and have not been able to find it there.

---

### Post by Chlodovechus on 2010-04-30
Copy and paste this into the terminal...
```
gconftool-2 --shutdown  && rm -rf ~/.gconf/apps/panel  && pkill gnome-panel
```
  
It should reset both of the panels back to normal.

---

### Post by Durandal512 on 2010-04-30
Wow.  Fast reply.  

Thank you!  That worked instantly!  I'll have to watch my itchy right-click more carefully.

Loving 10.04 so far (except for the longer boot time).

---

