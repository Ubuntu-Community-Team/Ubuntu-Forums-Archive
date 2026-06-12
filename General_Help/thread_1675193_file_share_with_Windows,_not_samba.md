---
title: "file share with Windows, not samba"
date: 2011-01-25
forum: General Help
---

### Post by qwertyjjj on 2011-01-25
I had a connection to my other Windows computer the other day automatically in the Places-->Network-->Windows Network folder but it now seems to have disappeared. I tried going to Place connect to server and typing in the WIndows computer name but it won;t connect and errors out.
Any ideas on what to do.
I also tried the IP:
Cannot display location "smb://%5C%5C192.168.1.36/"

---

### Post by dandnsmith on 2011-01-25
Were you connecting via a router, and do you have access to the internet from the Ubuntu PC? If so, are these features still working?
If they are, then you may be now blocking at the WindowsPC (even if you weren't before) - the firewall is the most likely culprit.
Try ping each way to test this.

---

