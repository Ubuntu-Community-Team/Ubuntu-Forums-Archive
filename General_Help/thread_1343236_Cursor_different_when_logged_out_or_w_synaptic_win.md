---
title: "Cursor different when logged out or w/ synaptic window has mouse over it?"
date: 2009-12-01
forum: General Help
---

### Post by khamil8686 on 2009-12-01
Its a minor problem, im just picky :)
My cursor changes to a huge cursor when i am at the login window after logging out or when i have synaptic package manager up and the mouse cursor is over it, it changes to this huge cursor
ive tried running

sudo gnome-appearance-properties
and changing the cursor for the super user to see if that helps, then when i log out it is the same way
its a cursor i downloaded from gnome-look so i copied my ~/.icons to /usr/share/icons so that the polar cursor set was available to the super user, i just checked what happens when i move the cursor over a synaptic window and i guess that part changed at least :) so now just wondering how to change the mouse cursor when no one is logged in, anyways thank you for any help :)

---------------------------------------

found that changing permissions of /usr/share/icons to 777 or so everyone can read write execute and then placing cursor themes in there and then changing through system>preferences>appearance i no longer have this problem, weird but whatever :) worked for me somehow!

---

