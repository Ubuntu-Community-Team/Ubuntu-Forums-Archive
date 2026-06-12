---
title: "XGL problem after install"
date: 2006-06-22
forum: General Help
---

### Post by kyoushu on 2006-06-22
I followed the tutorial found [here]("http://www.compiz.net/viewtopic.php?id=389") to install XGL but now when I boot it boots as normal but after the normal loading part, the GDM screen does not come up and a blue screen comes up saying that it > failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem? 

YES                   NO

There's to much info for me to type from the diagnosis so, when I press No it says > The X server is now disabled.  Restart GDM when it is configured correctly.

OK

When I press OK it goes to the terminal and nothing happens.  I can't type in anything because if I press a key nothing appears.  What can I do besides reinstall Ubuntu?

---

### Post by jnev on 2006-06-22
try going back to the nv driver instead of nvidia in your xorg.conf and see if you can start x after that. if you can you probably just need to reinstall your nvdia drivers. 

also, there is almost NEVER a need to reinstall linux. there is always a way to fix it, unlike windows.

---

### Post by kyoushu on 2006-06-22
I don't understand the first part, "try going back to the nv driver instead of nvidia in your xorg.conf and see if you can start x after that."

How would I do that?

---

