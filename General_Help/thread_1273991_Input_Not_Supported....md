---
title: "Input Not Supported...?"
date: 2009-09-24
forum: General Help
---

### Post by Pro$pect on 2009-09-24
After installing jaunty everything was fine, until I restarted that is. Now I'm getting a box floating around that says input not supported but everything seems to be working fine. How do I get rid of it? I have a nvidia 7800gtx and 64bit ubuntu.

---

### Post by nikhilk on 2009-09-24
> **Pro$pect said:**
> After installing jaunty everything was fine, until I restarted that is. Now I'm getting a box floating around that says input not supported but everything seems to be working fine. How do I get rid of it? I have a nvidia 7800gtx and 64bit ubuntu.

Probably the "HorizSync" and "VertRefresh" values are off. They should be present in the 'Section "Monitor"' of your xorg.conf file.

Check your monitor manual for the supported values.

---

