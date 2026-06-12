---
title: "Flash not in repository?"
date: 2009-11-16
forum: General Help
---

### Post by Redundant Username on 2009-11-16
I have everything in the sources list enabled, but flash isn't in the repository and it's been removed from Shiretoko, Chrome, Chromium, and Swiftfox. I don't know how to get my original version of Firefox either.

---

### Post by oldos2er on 2009-11-16
flashplugin-installer is in the mutltiverse repository. Have you tried updating your sources.list? ```
sudo apt-get update && sudo apt-get install flashplugin-installer
```

---

### Post by Redundant Username on 2009-11-17
Thanks, it works now.

---

