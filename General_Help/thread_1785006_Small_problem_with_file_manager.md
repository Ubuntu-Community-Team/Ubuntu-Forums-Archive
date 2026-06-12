---
title: "Small problem with file manager"
date: 2011-06-17
forum: General Help
---

### Post by TimmyK. on 2011-06-17
Hey everybody, on the the File Manager (I'm not sure which one, it's the GNOME default) the location bar at the top disappears every time I close and then re-open it, and I have to hit View/Location Bar to get it back. Is there a way to permanently keep it there? Thanks.

---

### Post by ruffEdgz on 2011-06-17
Try this command in your terminal to set the location bar to true:
```
gconftool -s -t bool /apps/nautilus/preferences/start_with_location_bar True
```
Run this code to see if the value did change:
```
gconftool -g /apps/nautilus/preferences/start_with_location_bar
```
If it returns 'true' then you should be set.

Cheers!

---

### Post by TimmyK. on 2011-06-17
Thanks, that did the trick!

---

