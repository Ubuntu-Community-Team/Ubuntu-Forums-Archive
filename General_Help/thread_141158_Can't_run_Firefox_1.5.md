---
title: "Can't run Firefox 1.5"
date: 2006-03-07
forum: General Help
---

### Post by woodsworth on 2006-03-07
Went through the "walk-through" on the Wiki, but when I start Firefox it's still 1.0.4. What did I miss? Is there a .deb package or some easier method of installation?

---

### Post by aysiu on 2006-03-07
Repeat this step: ```

sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
``` It basically tells Ubuntu, "When you see the command 'firefox,' use the new version instead of the old one."

Are you using Hoary, by the way? 1.0.4 isn't the Breezy version of Firefox?
Maybe you're still using the command ```
mozilla-firefox
``` instead of just ```
firefox
```?

---

