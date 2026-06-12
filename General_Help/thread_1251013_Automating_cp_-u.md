---
title: "Automating cp -u"
date: 2009-08-27
forum: General Help
---

### Post by jamesdcarroll on 2009-08-27
I found the cp -u command that says that it will "copy only when the SOURCE file is newer than the destination file or when the destination file is missing".  Sounds like a cheap and easy way to backup files to my NAS. What I would like to do, though, is create some kind of script that would do it for me (I've several directories) and even better do it as part of the normal shutdown process or maybe have the script call the shutdown process once its done. 

Is this possible?

Thanks,

---

### Post by Grenage on 2009-08-27
It is!  I would recommend rsync though.

---

### Post by kpkeerthi on 2009-08-27
Use rsync. You can automate it with a cron.

---

