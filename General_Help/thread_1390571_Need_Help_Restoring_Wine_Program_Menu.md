---
title: "Need Help Restoring Wine Program Menu"
date: 2010-01-25
forum: General Help
---

### Post by bdoe on 2010-01-25
Forgive me if this has been asked before. I tried searching, but all I got were tips on how to get the "Wine" and "Wine/Programs" menus to show up under Applications after they've been deleted. My problem is not that.

When I was running Jaunty, I had a number of Windows programs installed, and they would all show up properly under the Applications/Wine/Programs menu. However, since I had upgraded to Karmic, only new programs I've installed since the upgrade show up.

I had backed up ~/.local/share/applications/wine and restored it back after the upgrade, and can confirm that all of the .desktop files are there, along with the .desktop files of programs I've installed since. But none of the ones I restored from backup show up in the menus.

I remember running into this problem once before, and I found a command I could use that would re-scan the ~/.local/share/applications folder and rebuild the menus, and it worked great. But I cannot find it now.

Can anyone help me restore my Wine Programs menus? Or am I doomed to have to reinstall all my Windows apps every time I clean-upgrade Ubuntu?

---

### Post by 3rdalbum on 2010-01-25
```
update-menus
```

---

### Post by bdoe on 2010-01-25
Thanks. I think that's what the command was.

I just tried it and it didn't work, unfortunately. All of my "missing" menu items are now listed under Applications/Other.

*head-desk*

---

### Post by ricardisimo on 2011-01-08
```
update-menus: command not found
```

Any ideas? I searched synaptic for anything remotely resembling "update-menus"... nothing.

---

