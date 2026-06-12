---
title: "apt-get returns 404 errors with archive.ubuntu.com"
date: 2011-08-31
forum: General Help
---

### Post by virre on 2011-08-31
Trying to install Postgressql on my VPS that runs ubuntu server (jaunty) I get 404 errors, and also if I try update. At first after some looking I assumed this was due to an update to archive as there was a file that said it was in progress. I can no longer see that file so I assume the update is done but I still get the 404's 

Am I just impatient or should I fix something else.

---

### Post by kerry_s on 2011-08-31
Jaunty end of life was October 23, 2010, those repos are gone.

---

### Post by virre on 2011-08-31
wish my VPS provider would know that then. (Of course dist-upgrade don't work either. So time for backup and new install then)

---

### Post by kerry_s on 2011-08-31
> **virre said:**
> wish my VPS provider would know that then. (Of course dist-upgrade don't work either. So time for backup and new install then)

the new lts is version 10.04

---

### Post by virre on 2011-08-31
happily I could do-release-upgrade with localy mounting the jaunty iso and then sftping the .deb file so I should be able to step up to 10.04 with no problem now. 

Thank you.

---

