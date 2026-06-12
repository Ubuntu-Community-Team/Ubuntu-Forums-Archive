---
title: "software source issue"
date: 2009-10-07
forum: General Help
---

### Post by ub9876 on 2009-10-07
I have 2 3rd party software sources checked in my sources.
They are for updates to Google Chrome browser.They are different places..

Wine.budgetdedicated.com/apt hardy main
and
dl.google.com/linux/deb/stable main

anyone in the know.. do you see any problem with this..??
any conflicts..?
thanks

---

### Post by mac9416 on 2009-10-07
The first one seems fine. The second one obviously won't work, though. I get a 404 here: [http://dl.google.com/linux/deb/stable](http://dl.google.com/linux/deb/stable)

---

### Post by plucky on 2009-10-07
> **ub9876 said:**
> I have 2 3rd party software sources checked in my sources.
They are for updates to Google Chrome browser.They are different places..

Wine.budgetdedicated.com/apt hardy main
and
dl.google.com/linux/deb/stable main

anyone in the know.. do you see any problem with this..??
any conflicts..?
thanks

```
deb http://dl.google.com/linux/deb/ stable non-free main
``` for google apt repositories.

See this [link](http://www.google.com/linuxrepositories/apt.html)

Good Luck

---

### Post by fragos on 2009-10-07
That Google repo gives you multiple aps. You may want to consider [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main. Chromium is the open source project on which Linux Chrome is based. It is a daily update and always has features and fixes before they appear in Chrome.

---

