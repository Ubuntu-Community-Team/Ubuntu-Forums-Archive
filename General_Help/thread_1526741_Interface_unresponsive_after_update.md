---
title: "Interface unresponsive after update"
date: 2010-07-08
forum: General Help
---

### Post by charrah on 2010-07-08
After an update (and a restart), everything has become extremely sluggish to respond to my mouse and keyboard. It takes around 6 seconds to change a tab in Firefox, even changing windows will take 2 seconds before the new window will respond to typing (anything I type in the meantime simply doesn't appear).

Here is Synaptic's history from yesterday, I was wondering if any of the version numbers look off to somebody, or if somebody knows which is the offending package:

```
Commit Log for Wed Jul  7 17:20:30 2010


&#20197;&#19979;&#12398;&#12497;&#12483;&#12465;&#12540;&#12472;&#12364;&#12450;&#12483;&#12503;&#12464;&#12524;&#12540;&#12489;&#12373;&#12428;&#12414;&#12375;&#12383;:
acroread (9.3.2-lucid1) to 9.3.3-1lucid1
app-install-data-partner (12.10.04) to 12.10.04.3
chromium-browser (5.0.375.70~r48679-0ubuntu0.10.04.1) to 5.0.375.86~r49890-0ubuntu0.10.04.1
chromium-browser-inspector (5.0.375.70~r48679-0ubuntu0.10.04.1) to 5.0.375.86~r49890-0ubuntu0.10.04.1
libatk1.0-0 (1.30.0-0ubuntu2) to 1.30.0-0ubuntu2.1
libatk1.0-data (1.30.0-0ubuntu2) to 1.30.0-0ubuntu2.1
libatk1.0-dev (1.30.0-0ubuntu2) to 1.30.0-0ubuntu2.1
libatk1.0-doc (1.30.0-0ubuntu2) to 1.30.0-0ubuntu2.1
libjsch-java (0.1.42-1build1) to 0.1.42-1ubuntu0.1
libpam-modules (1.1.1-2ubuntu2) to 1.1.1-2ubuntu3
libpam-runtime (1.1.1-2ubuntu2) to 1.1.1-2ubuntu3
libpam0g (1.1.1-2ubuntu2) to 1.1.1-2ubuntu3
nautilus-dropbox (0.6.2) to 0.6.3
```

EDIT: Some Qt applications I tested (Anki, Clementine, Virtualbox) are still as snappy as they used to be.

---

### Post by charrah on 2010-07-09
Reinstalled Ubuntu. I think the problem had come from installing a newer version of Cairo from source, but I wasn't able to fix it that way.

---

