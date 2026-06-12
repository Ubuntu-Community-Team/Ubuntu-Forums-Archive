---
title: "WINE not working"
date: 2010-10-18
forum: General Help
---

### Post by kree8or on 2010-10-18
Hi, I've installed WINE, but when I click on a windows .exe file I get the following message:

[COLOR="Red"]"The file '/home/paul/Photoshop CS2 v9.0 ' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit."[/COLOR]

Any ideas?
Cheers
Kree8or

---

### Post by Irony on 2010-10-18
```
chmod -R 755 /home/paul/Photoshop CS2 v9.0
```

---

### Post by Quackers on 2010-10-18
Or, go to the .exe file invovlved and right-click and select properties. Under the permissions tab check the box "allow executing file as program".

---

