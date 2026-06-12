---
title: "ubuntu hangs when closing google chrome"
date: 2010-12-06
forum: General Help
---

### Post by starbala2008 on 2010-12-06
hi,
i am using latest google chrome stable version browser,whenever i close after using chrome ubuntu got hanged,i tried completely removing and reinstalling chrome but it doesnt work,closing chrome on anyway(by killing chrome using process id or using force quit option) results in hang. shutting down or restarting is the only thing i can do..system got totally hanged mouse,keyboard nothing works..

---

### Post by TeoBigusGeekus on 2010-12-06
Delete the config and cache files of chrome. Perhaps something in there makes your system hang.
```
rm ~/.config/chrome ~/.cache/chrome
```
Don't forget to export your bookmarks before you do this, as the above command will reset chrome to its initial state right after installation.

---

### Post by starbala2008 on 2010-12-06
:D problem solved! before seeing your reply i did kernel update,it solved the problem,anyway thanks 4 ur info.

---

