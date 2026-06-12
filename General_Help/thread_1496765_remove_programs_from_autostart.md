---
title: "remove programs from autostart"
date: 2010-05-29
forum: General Help
---

### Post by repsakkgn on 2010-05-29
how do i clear autostart? i've unchecked everything i don't need in "startup applications" but still after reboot i get everything running. i cleared ~./config/autostart but after reboot there appear all the default startup applicatons. What should i do?
and is there a way to remove volume indicator from indicator menu?

---

### Post by quixote on 2010-05-30
I'm not sure what to say about startup apps.  Unchecking them should have done it.  ???

The volume indicator is part of the "indicator-applet" which includes battery/AC icon and messaging icon. You'd remove that applet from the panel (right-click & select Remove).  Then you can get messaging icon alone by going to synaptic and installing the standalone "indicator-messages," and then adding it to the panel.  But I don't know how you'd get the battery/power icon back.  :(  The whole way they've made the indicators so horribly uncustomizable is beyond dumb.

---

### Post by formaldehyde_spoon on 2010-05-30
You can remove the Indicator app that has the volume control in it, then if you select when you want the battery icon in Power Management it will appear in the Notification Area app (assuming you still want that on your panel). 
  
If someone wants volume control (I know this doesn't apply to you OP) but doesn't want the Indicator app they can install gnome-volume-control-applet.

---

