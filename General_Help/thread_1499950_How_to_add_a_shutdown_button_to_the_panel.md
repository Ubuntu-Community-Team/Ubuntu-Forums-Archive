---
title: "How to add a shutdown button to the panel"
date: 2010-06-02
forum: General Help
---

### Post by heepie on 2010-06-02
I moved things around a bit and I added a top panel to make my lubuntu be more what I'm use to with gnome but I deleted the bottom panel and now I can't find a way to add a shutdown button to the panel...

any ideas???

---

### Post by MrMagne on 2010-06-14
You can do:
```
sudo vi /usr/share/applications/lubuntu-logout.desktop
```
and change ```
NoDisplay=false
``` and add ```
Categories=System;
```
Then you can add a new application launcher bar (don't know the exact english name), and in the system category you'll fin it...
... it took me a while to figure it out :mad:

---

### Post by heepie on 2010-06-14
Cheers mate, thanks a million

---

