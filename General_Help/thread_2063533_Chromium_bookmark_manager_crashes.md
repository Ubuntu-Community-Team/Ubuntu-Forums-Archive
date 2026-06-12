---
title: "Chromium bookmark manager crashes"
date: 2012-09-27
forum: General Help
---

### Post by geovino on 2012-09-27
I've noticed that the bookmark manager in Chromium browser crashes ever time I try to open it. 

I even uninstalled and reinstalled chromium-browser, but it still crashes. 


Any one else have this problem. Any fixes? 

Is there a profile file to delete to correct the problem?


running Ubuntu 12.04 64 bit and Chromium Version 20.0.1132.47

---

### Post by geovino on 2012-09-27
... just uninstalled chromium again and installed google chrome from their website. It has the same problem. So it must be a corrupted file on this computer. 

What could cause this?

---

### Post by Ingotian on 2012-10-23
Just done the same for me. Selected a bookmark I think might now not go anywhere and it tried for a while with screen "dimming" as all processor bandwidth taken then crashed. Crashed subsequently selecting any other bookmark.

---

### Post by drmrgd on 2012-10-23
Could be something corrupt with your configuration files (like .profile folder for Firefox), or at the very least just the bookmarks file.  If I'm not mistaken, even when you uninstall Chrome or Chromium, it still keeps that folder around and uses it upon reinstall.  

You could try to move that folder, relaunch Chrome / Chromium so it generates a new one, and then reimport your bookmarks.  I think in this regard Chrome and Chromium are the same, and if so the directory you're looking for is in ~/.config/google-chrome/Default.  Try to rename Default and re-run:

```
mv ~/.config/google-chrome/Default ~/.config/google-chrome/Default.bak
```

If that works, you can try to copy over things like the bookmarks and whatnot to see what's breaking it.  In the end, you may need to re-install your Extensions and other custom settings.  This might get you back up and running at least.

Alternatively, it it's really only the bookmarks that are causing problems, you might just replace the "Bookmarks" file with "Bookmarks.bak", which should be the last backed up version of them.  You might get lucky and find that this file is the only problematic one, and the backed up version is clean.

---

### Post by geovino on 2012-10-23
> **drmrgd said:**
> Could be something corrupt with your configuration files (like .profile folder for Firefox), or at the very least just the bookmarks file.  If I'm not mistaken, even when you uninstall Chrome or Chromium, it still keeps that folder around and uses it upon reinstall.  

You could try to move that folder, relaunch Chrome / Chromium so it generates a new one, and then reimport your bookmarks.  I think in this regard Chrome and Chromium are the same, and if so the directory you're looking for is in ~/.config/google-chrome/Default.  Try to rename Default and re-run:

```
mv ~/.config/google-chrome/Default ~/.config/google-chrome/Default.bak
```

If that works, you can try to copy over things like the bookmarks and whatnot to see what's breaking it.  In the end, you may need to re-install your Extensions and other custom settings.  This might get you back up and running at least.

Alternatively, it it's really only the bookmarks that are causing problems, you might just replace the "Bookmarks" file with "Bookmarks.bak", which should be the last backed up version of them.  You might get lucky and find that this file is the only problematic one, and the backed up version is clean.

Thanks, I'll that a try. 

I found that if I use CTRL+Shift+O the bookmark manager comes up with no crashing.

---

