---
title: "Disable Automount shares"
date: 2010-02-08
forum: General Help
---

### Post by altjx on 2010-02-08
When I'm browsing the network, I also get an icon that appears on my desktop as if I mapped their network drive to my desktop. I always have to manually right click it and click Unmount... Is there a way to avoid this?

---

### Post by mikewhatever on 2010-02-08
/apps/nautilus/desktop/volumes_visible

I think that's the setting that applies for all volumes, including network.

---

### Post by altjx on 2010-02-08
> **mikewhatever said:**
> /apps/nautilus/desktop/volumes_visible

I think that's the setting that applies for all volumes, including network.

How do I get there? I can't even change directories in terminal to apps, no such file or directory

EDIT: Got it. Had to unhide the Configuration Editor from System Tools
Problem solved, thanks...

Anyone else having this issue, right click Applications > Edit Menus. Go down to System Tools and put a check mark next to "Configuration Editor" and close that window. Go to Applications > System Tools > Configuration Editor... Once you have it opened, go to the location above, which is /apps/nautilus/desktop/volumes_visible and uncheck the box next to that one.

---

