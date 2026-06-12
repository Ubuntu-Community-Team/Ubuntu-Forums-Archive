---
title: "Ubuntu Software Center &amp; Update Manager Issues"
date: 2011-05-26
forum: General Help
---

### Post by quaunaut on 2011-05-26
So, for the past couple days, my Ubuntu Software Center has refused to open entirely. Clicking on the icon on the dock causes it to flash slowly a few times, before stopping and still not opening.

In addition, my Update Manager *does* start, but then when told to update things, fails at the point of clicking "Install Updates".

Any ideas here, as to how I can fix these issues?

---

### Post by TeoBigusGeekus on 2011-05-26
Try from command line to see if you get any error messages
```
software-center
```
and
```
sudo apt-get update
sudo apt-get upgrade
```

---

