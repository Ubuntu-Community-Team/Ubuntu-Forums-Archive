---
title: "changing the root directory for sftp users"
date: 2011-01-17
forum: General Help
---

### Post by yawnmoth on 2011-01-17
Say I have a user with SFTP access to /home/user01/.  If they go to /home/user01/../../home/user02/ they can see the contents of user02's directory.  What I'd like to do is to make it so they can't traverse up from /home/user01/ - so that, when they logon, via SFTP, /home/user01/ appears to them as /.

Any ideas as to how this might be done?

---

