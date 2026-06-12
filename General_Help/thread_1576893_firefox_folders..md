---
title: "firefox folders."
date: 2010-09-18
forum: General Help
---

### Post by soryu on 2010-09-18
can i get rid of those firefox folders in  /home/etc?
there's firefox,firefox3.0,firefox3.5

im using 3.6.10.

---

### Post by lovinglinux on 2010-09-18
No. You shouldn't remove system folders manually.

If they are bothering you, do this:

```
sudo apt-get purge firefox
sudo apt-get purge firefox-3.0
sudo apt-get purge firefox-3.5
sudo apt-get install firefox
```

This will remove any dummy packages and folders and leave you only with the latest Firefox folder.

If you are referring to /home/you/.mozilla/firefox-3.0, /home/you/.mozilla/firefox-3.5, then they contain your users profiles. Sometimes, depending on the Firefox version you install, it creates clones of your default profile folder, which is located at /home/you/.mozilla/firefox. You can delete the extra profiles folders if you are sure you are using the default.

---

