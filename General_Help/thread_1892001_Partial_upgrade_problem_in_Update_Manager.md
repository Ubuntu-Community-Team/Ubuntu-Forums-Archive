---
title: "Partial upgrade problem in Update Manager"
date: 2011-12-07
forum: General Help
---

### Post by kanishkdudeja on 2011-12-07
I havent been able to install all the available updates due to some partial upgrade problem..

Im attaching the screenshot.

Any suggestions as to how can it be fixed?

---

### Post by plucky on 2011-12-07
> **kanishkdudeja said:**
> I havent been able to install all the available updates due to some partial upgrade problem..

Im attaching the screenshot.

Any suggestions as to how can it be fixed?

From a terminal ```
sudo apt-get dist-upgrade
``` and look at what it is trying to remove before accepting the upgrade.If it is anything that might break your system (like removing ubuntu-desktop),do not accept the upgrade and post back the message.

Good Luck

---

### Post by kanishkdudeja on 2011-12-07
Got solved. It wanted to remove "Adobe Flash Plugin Downloader". I let it run. Thanks a lot. :)

---

