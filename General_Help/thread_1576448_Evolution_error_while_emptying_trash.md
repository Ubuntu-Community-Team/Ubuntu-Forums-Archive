---
title: "Evolution error while emptying trash"
date: 2010-09-17
forum: General Help
---

### Post by nmyrick on 2010-09-17
Can anyone help me with this error.  The folder that this refers to does exist, so I dont know why I'm getting this error when I try to empty my trash in Evolution.

---

### Post by dcstar on 2010-09-18
> **nmyrick said:**
> Can anyone help me with this error.  The folder that this refers to does exist, so I dont know why I'm getting this error when I try to empty my trash in Evolution.

That is the standard location for the default Sent items mailbox, if that does not exist on your system then you have bigger problems than Trash.

---

### Post by claracc on 2010-09-18
You can try this:

Close evolution, go to places, your personal folder, then mark in see hidden files, go to .evolution, mail, local. There you delete folders.db

Open evolution and try to empty trash again.

---

### Post by nmyrick on 2010-09-18
Thanks Claracc, that worked.  All my other folders in Evolution work fine, including the 'Sent Items' folder, so apparently that was the only issue.

---

### Post by JohnPta on 2010-10-07
Thanks Claracc also from my side your idea works. However when you delete a file again, to trash, you have to go through the whole exercise again.

---

### Post by nmyrick on 2010-10-11
JohnPta,

I haven't had that problem. What Claracc posted worked as a permanent fix for me.  

You may try uninstalling and re-installing Evolution.  I would run a backup first, but if you **_don't_** do the complete uninstall through the synaptic package manager, it should keep all of your folders, emails, and settings.  

Just run the uninstall through Ubuntu Software Center (which doesn't completely uninstall anything), and then restart your computer and re-install.  The computer restart may not be required, but it is a good practice when uninstalling software.

---

