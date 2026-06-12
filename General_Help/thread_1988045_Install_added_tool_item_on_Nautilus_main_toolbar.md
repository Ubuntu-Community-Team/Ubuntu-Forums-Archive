---
title: "Install added tool item on Nautilus main toolbar"
date: 2012-05-26
forum: General Help
---

### Post by Ralph L on 2012-05-26
Under lucid I installed an additional tool item on the Nautilus toolbar as follows:
1. Save the file /usr/share/nautilus/ui/nautilus-navigation-window-ui.xml in its current location under the name nautilus-navigation-window-ui.xml.old
2. Enter sudo gedit /usr/share/nautilus/ui/nautilus-navigation-window-ui.xml
3. Add to the Toolbar/toolitem section:  <toolitem name="New Folder" action="New Folder"/>
4. Restart the computer if necessary.

Under precise pangolin 12.04 this file has been moved or done away with.  Anybody know how to add a new tool item to the Nautilus main toolbar under 12.04?

---

