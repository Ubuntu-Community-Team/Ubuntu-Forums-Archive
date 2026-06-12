---
title: "can't change file attributes in samba share"
date: 2009-11-10
forum: General Help
---

### Post by gaspedalo on 2009-11-10
Guys, please help me. i'm running out of ideas.
I rsynced -a a folder structure from a ubuntu server machine to a ds508 (synology nas) samba share. And now all my folders are set to be "hidden" and "system" to the Windows Clients. The Client may not touch these attributes and I don't know how to define the attribute from within the nas ssh shell. ANY ideas are apprecieated. :cry:

---

### Post by alphaniner on 2009-11-10
Does your NAS have a smb.conf file?  If so, could you post it here?

---

### Post by gaspedalo on 2009-11-11
I didn't want to touch the smb.conf because the nas is working out of the box an I'm quite sure that there's nothing wrong with the smb.conf (I have a lot of shares that do work).
I found a solution, the problem is the rsync transfer over smb shares, that probably mixes uo all the attributes. So I synced the data via rsync daemon running on the nas...and voila everything's in place as it should.

---

