---
title: "Uninstall KDE packages"
date: 2009-08-03
forum: General Help
---

### Post by frt975 on 2009-08-03
I want to uninstall KDE and all associated packages besides the games and educational stuff. I also don't want to uninstall KDE and reinstall the games as for I'll have to reorganize/rename them. Thanks in advance.

---

### Post by Sxeptomaniac on 2009-08-03
That might not be possible.  You can try removing the "kubuntu-desktop" package, which should get rid of it all, but if any of the games you want depend on KDE, they will be removed as well.

---

### Post by frt975 on 2009-08-04
I uninstalled Dolphin witch uninstalled a bunch of meta-packages but didn't uninstall the games/educational stuff.:lolflag:

---

### Post by Zorael on 2009-08-04
kubuntu-desktop is a virtual package; removing it won't really remove anything, but installing it will install the Kubuntu desktop bundle. I'd suggest you remove KDE completely and then reinstall the apps you want.

I'm not sure what you mean by "reorganize/rename", but if you made changes to their application menu entries, those will persist even if you remove the apps they link to. To explain, those menu entry changes are specific to your user, and hence they reside in your home directory. Removing packages should never touch what's in there.

That's why you can get remnant application menu entries (pointing to Firefox or whatever) even after removing that app itself; again, the custom menu entry is saved where the package removal script won't ever meddle.

---

