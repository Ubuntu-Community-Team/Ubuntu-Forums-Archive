---
title: "useradd -- default shell"
date: 2010-01-27
forum: General Help
---

### Post by oospill on 2010-01-27
when I use the 'useradd' command, the default shell for the new user is /bin/sh instead of /bin/bash .. how do I prevent this from happening?  And, do I change a user's default shell just by editing /etc/passwd?

thanks!
oospill

---

### Post by bluefrog on 2010-01-27
adduser instead of useradd

can edit /etc/passwd or usermod -s /bin/bash user

---

