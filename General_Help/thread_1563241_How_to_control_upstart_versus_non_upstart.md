---
title: "How to control upstart versus non upstart"
date: 2010-08-28
forum: General Help
---

### Post by SanDiegoSeahawk on 2010-08-28
I'd like to ensure that avahi-daemon launches after afpd/netatalk during boot.  

avahi-daemon is an upstart job and afpd/netatalk is not. 

Is there any way to control when the avahi-daemon launches so that it always launches after afpd/netatalk?

I've searched on this a bit and have found very little on the subject.  It seems that not all services have been adapted to upstart so I can't imagine this is a new requirement.

Any thoughts?

---

