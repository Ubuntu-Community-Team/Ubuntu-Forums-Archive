---
title: "Links won't open"
date: 2009-08-13
forum: General Help
---

### Post by bilboe on 2009-08-13
Hello everyone. Recently, my firefox got somewhat messed up, but now it is fixed. However, despite it being my default browser in "sudo update-alternatives --config x-www-browser" whenever i click a link in an external application, instead of opening firefox, it just does nothing.

Any ideas?

Thank you!

---

### Post by wojox on 2009-08-13
```
sudo update-alternatives --set x-www-browser /usr/bin/firefox
```

See if that works.

---

### Post by bilboe on 2009-08-13
No that does not, but thank you. Any other ideas?

---

### Post by CatKiller on 2009-08-13
System &#8594; Preferences &#8594; Preferred Applications &#8594; Internet &#8594; Web Browser. Set it to Firefox.

---

