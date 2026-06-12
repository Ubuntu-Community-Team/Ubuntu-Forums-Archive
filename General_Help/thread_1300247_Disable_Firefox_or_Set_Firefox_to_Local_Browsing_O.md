---
title: "Disable Firefox or Set Firefox to Local Browsing Only"
date: 2009-10-24
forum: General Help
---

### Post by XP1 on 2009-10-24
**Disable Firefox or Set Firefox to Local Browsing Only**

Rather than uninstall, how do I disable Firefox or set Firefox to Local Browsing Only?

I want to accomplish this without any add-ons or extensions.

Is there a setting in **about:config**?

---

### Post by XP1 on 2009-10-25
I just put "**pref("general.config.filename", "disable");**" at the end of "**/usr/lib/firefox-3.5.3/defaults/preferences/firefox.js**" to stop Firefox from loading.

I tried locking the broswer.offline setting to always true, but Firefox seems to allow users to override that locked setting.

---

