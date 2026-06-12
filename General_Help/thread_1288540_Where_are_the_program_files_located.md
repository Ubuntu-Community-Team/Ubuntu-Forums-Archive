---
title: "Where are the program files located?"
date: 2009-10-11
forum: General Help
---

### Post by viking_maniac on 2009-10-11
When I recently installed RealPlayer 11, the install wizard asked me where to install the program. What would be the appropriate directory to install software/program files in Linux?

---

### Post by madsmeg on 2009-10-11
It is odd for it to ask for you to install it to such a location, i presume you downloaded the linux version? They may have just not changed the directories in the auto wizard. I would just install it into your /home folder.

---

### Post by oldos2er on 2009-10-11
I prefer it in /opt

---

### Post by mcduck on 2009-10-11
> **viking_maniac said:**
> When I recently installed RealPlayer 11, the install wizard asked me where to install the program. What would be the appropriate directory to install software/program files in Linux?

All the peograms installed from Ubuntu's native packages (.deb) are installed all around the filesystem, each file into different place depending on the file's actual purpose. So there isn't any single location for programs like there is in Windows.

For things installed manually or from binary installers the best place would be either somewhere in your home directory, or /opt as suggested above. (/opt is pretty much a standard place for system-wide installs of things that don't really belong into the system and that come from outside of the distribution).

---

