---
title: "setting up web server in 9.04 desktop"
date: 2009-09-08
forum: General Help
---

### Post by b89.smith on 2009-09-08
I have a web server (Apache2) currently running on my Ubuntu machine.  The  web servers folder is /var/www/. I recently added an additional drive to my server that is mounted at /media/drive2.
Is there a way that I can have this secondary drive placed in a virtual folder at /var/www/drive2 so that when I browse [http://localhost/drive2/index.html](http://localhost/drive2/index.html) it is actually showing me the file located at /media/drive2/index.html.

Thanks

---

### Post by holiday on 2009-09-08
You could put a symlink to your new drive in /var/www

ln -s /media/newdrive /var/www/newdrive

You'll have to set the access permissions on the new drive to the same as those on /var/www

---

