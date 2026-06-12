---
title: "Samba Question."
date: 2010-05-12
forum: General Help
---

### Post by Roasted on 2010-05-12
I've always ran Samba, which basically allows me and my Mac laptop, Windows boxes, and Linux boxes to all hit the same source. Very handy.

Typically in the past when I rebooted and users had been connected to it I would get a screen saying I had to type in my root PW to reboot due to the fact users were still connected to the server.

Now, it's very possible that nobody is connected to it, but I almost always had to type in my password to reboot. This prompted a question in my mind. What causes that? Is it because of the auto-sync software I use in Windows? I'm pretty sure there's an option to "Disconnect after synchronizing" but I'm not sure if I have it enabled or not.

Anyway, I'm just curious if it's a Samba related thing or if it's something on the Windows boxes. That's all. Thanks guys.

---

### Post by blueridgedog on 2010-05-12
I think it is Linux telling that another user has a file open.  That said, you can mock it up by opening a file on your mac, then attempting a reboot.  Repeat with a windows system.

---

### Post by Roasted on 2010-05-12
My file server is used for backup purposes only. No users should have files "open". They auto-sync at 3 am every morning without them even knowing. Not sure how any files would be "open..."

---

### Post by blueridgedog on 2010-05-12
Perhaps a copy that did not finish neatly?  Do you see any open files using lsof?

---

### Post by Roasted on 2010-05-13
No? I don't know what lsof is. The synchronizing either works or it doesn't, it doesn't "hang" at all...

---

