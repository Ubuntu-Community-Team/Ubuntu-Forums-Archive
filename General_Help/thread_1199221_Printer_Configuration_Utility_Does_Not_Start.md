---
title: "Printer Configuration Utility Does Not Start"
date: 2009-06-28
forum: General Help
---

### Post by cooper_d on 2009-06-28
Hi,

I have installed Ubuntu 9.04 and I managed to add my printer fine before the update manager downloaded many updates.  Now the System > Administration > Printing application does not start as expected.  When I select it, it appears briefly in the bar at the bottom of the screen and then disappears.

Any idea how to resolve this?

Many thanks,
Dave.

---

### Post by -kg- on 2009-06-28
What kind of printer?  If it's an HP (hopefully) you might try installing hplip-gui from the repos.  When you first run this, it will ask you to "discover" the printer, at which point it is made the default printer and the icon should appear in the Notification Area on the top panel.

That's the way it worked for me.

Of course, I was able to print from various software anyway.  Have you tried printing from say Oo Writer or the PDF viewer?

---

