---
title: "do you have to use root crontab for updatedb?"
date: 2006-05-05
forum: General Help
---

### Post by jms830 on 2006-05-05
do I have to use the root crontab in order to periodically do the "updatedb" command (and other commands that require sudo)? it requires sudo, so I'm assuming yes... 
however in this howto [http://ubuntuforums.org/showthread.php?t=102626](http://ubuntuforums.org/showthread.php?t=102626) it implies that you just can use the crontab for your user.

---

### Post by kaamos on 2006-05-05
Updatedb runs as root every day at 2 am. But yes, I think you should use the root crontab.

---

