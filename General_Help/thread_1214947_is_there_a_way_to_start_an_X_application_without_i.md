---
title: "is there a way to start an X application without it appearing in the taskbar panel?"
date: 2009-07-16
forum: General Help
---

### Post by frankdn on 2009-07-16
Subject says it all, really.   I prefer an analog desktop clock, so I added this script to System->Preferences->Startup Applications:

  #!/bin/bash
  nohup xclock -geo 64X64-0-0 &

Just one little nit: an 'xclock' session appears in the bottom panel, along with all the other apps.  Is there a way to prevent this without deleting the entire panel?

Thank you!

---

### Post by gettinoriginal on 2009-07-16
there are desklets for desktop apps such as clock  :P

```
sudo apt-get install gdesklets
sudo apt-get install gdesklets-data
```

---

### Post by frankdn on 2009-07-17
Very nice!  Thank you!

---

