---
title: "Problem with all KDE applications after upgrade"
date: 2010-11-06
forum: General Help
---

### Post by DrScum on 2010-11-06
Starting a while ago after some upgrade kde applications (like k3b and Amarok) are no longer running properly. The error message indicates something along the lines of insufficient permission in target directory and points to a full hard drive. The harddrive is definitely not full so I assume some permission problem. Can anyone help me out here?

---

### Post by DrScum on 2010-11-08
meanwhile, after some researching and thinking I logged on as root and did change ownership recursively of the .kde directory in /home/ewald
The error messages didn't appear after that except one which said the bookmarks file couldn't be updated. I hope the applications are working now.

---

