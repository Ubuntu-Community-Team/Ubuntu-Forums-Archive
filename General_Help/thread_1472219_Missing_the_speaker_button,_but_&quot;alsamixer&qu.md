---
title: "Missing the speaker button, but &quot;alsamixer&quot; works?"
date: 2010-05-04
forum: General Help
---

### Post by schwabdale on 2010-05-04
When I open a terminal and type alsamixer, it works, but on my bar I do not have the speaker icon.

Please help.

---

### Post by Seal Daemon on 2010-05-04
Haven't used Gnome for a while now so don't know how it was called but you need to add an applet for that.

---

### Post by lotharmat on 2010-05-04
In Lucid you need to add the Indicator applet - this contains the vol control!

---

### Post by inameiname on 2010-05-04
I found this when I was in search of a resolution to the same problem.  And it seems to work:

                                 go to System > Preferences >  Startup Applications

in the startup tab, look for 'Volume Control' and check it if its  unchecked.

If its not there, 'Add' it using the following parameters:

Name: Volume Control
Command: gnome-volume-control-applet
Comment: Show desktop volume control

...and then restart....


This is what I used and it's back to the same as it was in Karmic for me.

---

### Post by schwabdale on 2010-05-04
> **lotharmat said:**
> In Lucid you need to add the Indicator applet - this contains the vol control!

That was it! Thanks!

---

