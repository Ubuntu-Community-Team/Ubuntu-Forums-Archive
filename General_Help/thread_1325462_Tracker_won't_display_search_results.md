---
title: "Tracker won't display search results"
date: 2009-11-13
forum: General Help
---

### Post by naked on 2009-11-13
I've had this problem for a while, but figured I'd wait to see if the recent upgrade fixed it.  It didn't.  I've purged, and reinstalled the packages.  I'm currently running the most recent updates on Karmic.  Any thoughts?

See the attachment for a screenshot.  It shows I have results, and I can page through them, but the window is always blank.

L

---

### Post by FuturePilot on 2009-11-13
Yeah, I've seen that happen many times before. Usually a re-indexing should fix it. Right click on the Tracker applet on the panel and select re-index.

---

### Post by naked on 2009-11-13
Thanks for the quick response.  I can't seem to get the applet to show up?  There isn't a display option anymore in the preferences?  

Is there a way to reindex through the command line?

---

### Post by FuturePilot on 2009-11-13
If you press Alt-F2 and enter "tracker-applet" does it show up? If not you can try the command ```
tracker-processes -r
``` which will re-index everything.

---

### Post by ajgreeny on 2009-11-13
The command line entries you need to stop trackerd and reindex files are
```
killall trackerd
trackerd -v 2 -R
```
I think you need the tracker applet in your startup list to have it show on the panel, so look in **System -Preferences _Startup Applications** and add it if needed.

---

