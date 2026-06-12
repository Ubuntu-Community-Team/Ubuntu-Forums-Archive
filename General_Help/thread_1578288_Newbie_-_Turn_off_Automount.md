---
title: "Newbie - Turn off Automount"
date: 2010-09-20
forum: General Help
---

### Post by Quarkrad on 2010-09-20
Sorry if this is easy.  I have a camera that when connected to Ubuntu 10.04 is recognised but unable to interface/download picture to digikam (the photo application).  The solution is to launch Nautilus and unmount the camera - that comes up as USP PTP.  When I do this everything works like a charm.  Is there a way to 'tell' Ubuntu not to mount this specific device when it is connected?  Thanks.

---

### Post by pastalavista on 2010-09-20
[Alt+F2] gconf-editor-->apps/nautilus/preferences & uncheck "automount media"

---

### Post by Quarkrad on 2010-09-20
Many thanks :)

---

