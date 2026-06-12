---
title: "can't change permission for /var/www"
date: 2011-09-11
forum: General Help
---

### Post by tech7 on 2011-09-11
I've tried changing them via file browser as root.
I've tried changing them via terminal with chmod.
For some reason, I cannot get the /var/www directory or it's contents to change permissions.
I'm using Ubuntu 10.04 which I installed on this machine last night.
I've done this on Ubuntu countless times before without any problems.
Any suggestions or insight would be greatly appreciated as I really need to start working on the contents of these directories without having to login as root and run all my applications as root.
Thanks!

---

### Post by mue.de on 2011-09-11
Maybe the apache2 server is running, thus using that directory; try an 

> sudo service apache2 stop

---

