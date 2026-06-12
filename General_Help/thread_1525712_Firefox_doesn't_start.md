---
title: "Firefox doesn't start"
date: 2010-07-07
forum: General Help
---

### Post by frecon on 2010-07-07
Ubuntu 10.04
Firefox 3.6.6 (apt-get firefox)

Firefox doesn't start anymore. Started yesterday. Can't remember what I was doing at the time. Tried reinstalling. Nothing comes up. If I run firefox from the terminal nothing happens. No text shows. I've tried starting it with some parameters like -safe-mode, -jsconsole, --debug but nothing works. Is there something else I can try? I can't do my work now because of this issue.

---

### Post by philinux on 2010-07-07
Try renaming your ~/.mozilla folder to .mozilla.backup

You can retrieve you bookmarks from the backup folder if firefox will run with a new profile folder.

---

### Post by frecon on 2010-07-07
Yeeeeees! Thank you philinux!

---

