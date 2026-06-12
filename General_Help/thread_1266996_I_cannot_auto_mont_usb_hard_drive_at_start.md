---
title: "I cannot auto mont usb hard drive at start"
date: 2009-09-15
forum: General Help
---

### Post by linuck on 2009-09-15
Hi! 
My problem is that I can't have my USB hard drive mount at start up.
 
I have a minimal installation of ubuntu jackalope with XBMC that start automatically in standalone mode with a ".xsession" who contains this line
 
exec xbmc standalone
 
This part works fine, my xbmc starts up automatically.
 
The problem is that once xbmc is started up, I have to open a session in another terminal to mount the hard drive, because this line in the fstab doesn't work.
 
/dev/sdb1 /media/LaCie ext3 auto,defaults 0 0
 
I have no GUI at all.
Is there someone who have an idea?
I have one user, xbmc. XBMC starts up with this user.

---

### Post by coller_girl on 2009-09-15
Have you Tried fdsk or looked here?

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

