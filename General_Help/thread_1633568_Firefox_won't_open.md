---
title: "Firefox won't open"
date: 2010-11-29
forum: General Help
---

### Post by joelstitch on 2010-11-29
I installed the add-on Greasemonkey for Firefox and since then firefox won't open. If I try to open it on safe mode nothing comes up, it I try it a secont time it tells me that Firefox is already running and if I try to open it normally it shows it on the bottom as if it was openning and then it dissapears. Any suggestions?

---

### Post by mikewhatever on 2010-11-29
Addons are a frequent cause of Firefox related problems. You should probably create a new profile and then migrate settings from the old one if needed.

killall firefox && killall firefox-bin

firefox -P

...and create a new profile.

---

