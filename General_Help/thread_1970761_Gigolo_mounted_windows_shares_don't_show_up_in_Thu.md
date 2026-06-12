---
title: "Gigolo mounted windows shares don't show up in Thunar side pane"
date: 2012-05-01
forum: General Help
---

### Post by kpuz on 2012-05-01
I am able to mount windows shares at work using gigolo but they do not show up in the convenient shortcut location in thunar (this feature is present in nautilus).  I was wondering if this is normal or if I need to tweak somthing to make this happen.

---

### Post by Morbius1 on 2012-05-01
Thunar doesn't do that but you can create a link to the mount point location:

Open Thunar and find the .gvfs folder in your home directory. Then drag it to the left side panel. 

All of it's remote shares will be mounted under the 'gvfs folder.

---

### Post by Jose Catre-Vandis on 2012-05-02
Double click on the share in gigolo will open new thunar window with share

---

