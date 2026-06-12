---
title: "Edit permissions for /var/www/ ?"
date: 2010-05-06
forum: General Help
---

### Post by h4x0rmx on 2010-05-06
I have apache2 running on my computer. I want to change the permissions for /var/www/ so that I can edit the files without a problem. Right now I can use the gksudo command, but I'd like to be able to have all the files available when using an IDE like eclipse.
I've read in several places that ```
chmod 755 /var/www
``` will do, but if I'm not mistaken that would give read/write access to anyone. I'm not in a production environment, so I'm not too worried about security, but I'd like to give anyone else as less permissions as possible. Would this be possible?
I'll appreciate any help!

---

### Post by utnubuuser on 2010-05-06
If this is just for a home development server....

first thing I usually do is > sudo chown -R myusername /var/www

That allows me to do anything in /www.
 
A good file-permissions page:> [http://www.cyberciti.biz/faq/how-linux-file-permissions-work/]("http://www.cyberciti.biz/faq/how-linux-file-permissions-work/")
A better one:> [http://www.zzee.com/solutions/linux-permissions.shtml#numeric]("http://www.zzee.com/solutions/linux-permissions.shtml#numeric")
> [https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions")Community documentation wiki
755 is read+write+execute for owner, read+execute for group and everyone else
644 is read+write, read, read

---

### Post by h4x0rmx on 2010-05-06
Thanks utnubuuser!

---

