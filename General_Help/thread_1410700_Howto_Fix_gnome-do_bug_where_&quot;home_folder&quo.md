---
title: "Howto: Fix gnome-do bug where &quot;home folder&quot; does not open Nautilus"
date: 2010-02-19
forum: General Help
---

### Post by e.m.fields on 2010-02-19
If you've run into this bug post-Intrepid where gnome-do does not do anything after selecting "home folder", I found the solution in this bug thread:
[https://bugs.launchpad.net/do/+bug/290136]("https://bugs.launchpad.net/do/+bug/290136")

See comment #55 for a permanent solution.
[https://bugs.launchpad.net/do/+bug/290136/comments/55]("https://bugs.launchpad.net/do/+bug/290136/comments/55")

Busby  wrote on 2009-11-05:  	  #55
> 
For a single command fix that persists forever and doesn't require super user privileges, use this command:

cat /usr/share/applications/nautilus-home.desktop | perl -pe 's/Exec=nautilus --no-desktop/Exec=nautilus --no-desktop ./g;' > $HOME/.local/share/applications/nautilus-home.desktop

This will basically create a corrected version of the faulty launcher in your home directory which will override the system's launcher.


---

### Post by Pseudo-Morph on 2010-03-08
Thank-you, a most helpful pointer. :)

---

