---
title: "Seeking advice on setting Gnome Panels for new users"
date: 2010-04-08
forum: General Help
---

### Post by Azdour on 2010-04-08
Hi all,

I've started writing a script that can create users and depending on certain parameters, set the panel in those user accounts to different types, i.e.:

restricted - cannot change the panels, cannot switch user
base - no panels just icons shortcuts on the desktop to launch specific apps

The script would:
 - create the user
 - use gconftool-2 to apply restrictions
 - use gconftool-2 to import the panel to be used

I'm looking for advice as to if this is the best solution or fo any other avenues to explore.

I've also started to play with a basic script to create a user and use gconftool-2, but I've noticed some issues:

 - when you create a user from scratch they have no '.gconf' and therefore no settings. I copy in a basic .gconf into the new user and then can use gconftool-2, is there a better way?
 - if you set suspend and hibernate to false, they still seem to appear in the dialog that pops up when you hit the computers power button
 - I've set up a panel with the no switch-user app, but has the shutdown button. When I create a user with this panel sometimes the shutdown button is not there and so the user cannot easily shutdown the machine

I think many of my issues stem from the fact that the new user initially has no '.gconf', so finding a better way of providing it may solve them.

Thanks in advance.

---

