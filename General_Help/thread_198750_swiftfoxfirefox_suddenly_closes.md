---
title: "swiftfox/firefox suddenly closes"
date: 2006-06-17
forum: General Help
---

### Post by moore.bryan on 2006-06-17
i installed swiftfox a while, was very happy, but it suddenly started closing for no reason.  i removed all the extensions/plugins, but it would still crash.  i uninstalled swiftfox, reinstalled firefox and it happened there too.  i would have posted more info, but i'm not even sure where to begin...

---

### Post by kalata on 2006-06-17
happens to me too... mainly when video plugin is started but sometimes without it too...

---

### Post by vigleik on 2006-06-17
[QUOTE=moore.bryan]i installed swiftfox a while, was very happy, but it suddenly started closing for no reason.  i removed all the extensions/plugins, but it would still crash.  i uninstalled swiftfox, reinstalled firefox and it happened there too.  i would have posted more info, but i'm not even sure where to begin...[/QUOTE]

To make sure there are no residual bad extensions, plugins or settings, you have to remove (or just move) the .mozilla directory. Then firefox (or swiftfox) will truly start from scratch the next time you launch it, and you can experiment with reinstalling extensions, installing flash, and so on. Firefox and swiftfox both read the .mozilla directory when they start, so if there's some badness there (I have no idea what, but it happens) it's likely to affect both.

Vigleik

---

### Post by moore.bryan on 2006-06-18
vigleik... that's what i did...

---

