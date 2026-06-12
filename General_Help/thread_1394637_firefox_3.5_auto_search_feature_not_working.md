---
title: "firefox 3.5 auto search feature not working"
date: 2010-01-30
forum: General Help
---

### Post by jaden93 on 2010-01-30
hello, recently in firefox, the auto search feature has stopped working. usually when i type in a random name like "cooking" it sends me to a website that deals in cooking. but now when i type in cooking i dont see anything but this warning```
 Firefox can't find the file at jar:file:///usr/lib/firefox-3.5.7/chrome/en-US.jar!/locale/browser-region/region.propertiescooking
``` i dont know why it keeps doing this, and ive checked the about:config files, it says the auto search feature is on and everything. can someone please help.

---

### Post by lovinglinux on 2010-01-31
Re-install Firefox with this command:

```
sudo apt-get install --reinstall firefox-3.5
```

That should take care of the missing file.

---

