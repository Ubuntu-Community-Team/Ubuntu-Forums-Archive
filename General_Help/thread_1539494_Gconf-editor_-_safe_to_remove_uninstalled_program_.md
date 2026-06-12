---
title: "Gconf-editor - safe to remove uninstalled program entries?"
date: 2010-07-26
forum: General Help
---

### Post by culfunius on 2010-07-26
Is there any risk to deleting program entries from gconf-editor? It's very busy with software I've uninstalled, which makes it fractionally harder to find entries when I want to edit them.

---

### Post by ajgreeny on 2010-07-26
I don't think you can remove them directly using gconf-editor, but you can delete the appropriate subfolder from the ~/.gconf folder without problems.

Just remember, however that you would lose any configurations you have set up and perhaps might want to keep in case you should reinstall the package.

---

