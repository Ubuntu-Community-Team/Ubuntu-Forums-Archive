---
title: "Firefox Back Button Has No Icon"
date: 2011-05-03
forum: General Help
---

### Post by paulmdavies on 2011-05-03
I've installed 11.04 as an upgrade to 10.10. Now, the back/forward buttons in Firefox have no icons, which means they're hard to find, and they're also much thinner than usual. Also, the home button has disappeared and I can't put it back from the customize menu.

I've reinstalled Firefox to no avail. Does anyone have any ideas?

---

### Post by lovinglinux on 2011-05-03
First, check if your browser theme is not responsible for the missing button images. Open the Add-ons Manager, select the "Appearance" tab, select the "Default" theme and enable it. Restart Firefox.

If that doesn't help, close Firefox, find your user profile folder under **~/.mozilla/firefox** and delete the file **localstore.rdf**. Restart Firefox.

---

### Post by blueeyesmike on 2011-05-03
Same problem here. Using other themes fixes the problem but I would prefer to get the default theme back.

---

### Post by lovinglinux on 2011-05-03
> **blueeyesmike said:**
> Same problem here. Using other themes fixes the problem but I would prefer to get the default theme back.

Have you tried to delete the localstore.rdf file?

---

