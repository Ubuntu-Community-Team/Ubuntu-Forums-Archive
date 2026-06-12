---
title: "Firefox browser accessing Ubuntu start page so I have lost my bookmark access"
date: 2012-10-13
forum: General Help
---

### Post by allen76693 on 2012-10-13
Obvious I did something unintentional that when I click on Firefox in 12.04 it brings me automatically to Ubuntu start page with no access to mt bookmarks. Could someone tell me how to un-do this.
Thank you from a challenged and embarrassed user

---

### Post by ajgreeny on 2012-10-13
It sounds as if you have removed the hidden .mozilla folder in your home.  See if you can find it again with ```
find -type d -name .mozilla
```which may show you more than one.

---

