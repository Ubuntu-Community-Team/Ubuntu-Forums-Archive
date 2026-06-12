---
title: "Hot to get rid of Chrome as browser for Thunderbird?"
date: 2011-11-22
forum: General Help
---

### Post by Freek07 on 2011-11-22
Among other browsers I have chrome.
Firefox is default- in KDE (I'm KDE user), /etc/alternatives/www-browser points to FF, click on URL in every app but thunderbird opens FF as I want it to.

But in thunderbird, it keeps opening in chrome.

Any ideas where can I fix it?

---

### Post by jjex22 on 2011-11-22
As you have to add chrome, it's probably changed thunderbird's defaults - try opening firefox and going preferences->advanced and clicking the check now button for make default?

Hope it helps.

---

### Post by skit85 on 2011-11-22
If you go to system settings and Default applications, what is your default web browser set to?

---

### Post by Freek07 on 2011-11-22
> **jjex22 said:**
> As you have to add chrome, it's probably changed thunderbird's defaults - try opening firefox and going preferences->advanced and clicking the check now button for make default?

Hope it helps.

Whoa, that fixed it.
Any idea where could those settings be? In KDE system settings/default apps AND gconf-editor it was firefox...
Maybe it's a thunderbird-specific setting...

---

