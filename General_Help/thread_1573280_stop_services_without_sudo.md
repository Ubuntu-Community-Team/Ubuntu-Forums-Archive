---
title: "stop services without sudo?"
date: 2010-09-12
forum: General Help
---

### Post by becatlibra on 2010-09-12
I am working on a notebook which has both gnome and wmii.  I am trying to find a way to script stopping various services when booting into wmii however the "service xxx stop" requires sudo

Is there a way to allow a user to manage services without the need for sudo (aside from password-less sudo)?  I assume there are permissions complications with writing the PIDs, etc.  Is there a 'simple' solution?  Even possible passwordless sudo just for the 'service' command?

Thanks

Benjamin

---

### Post by llamabr on 2010-09-12
It would require editing groups.  Which services?  And why don't you want to use sudo?  The filesystem is set up the way it is for good reason.

---

### Post by Rubi1200 on 2010-09-12
> **llamabr said:**
> It would require editing groups.  Which services?  And why don't you want to use sudo?  The filesystem is set up the way it is for good reason.
+1 about sudo and filesystem privileges.

As llamabr remarks, you would need to be more specific about which services.

Thanks.

---

