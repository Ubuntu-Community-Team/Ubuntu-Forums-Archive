---
title: "Simple permissions question &amp; Apache2"
date: 2009-06-30
forum: General Help
---

### Post by deekthesqueak on 2009-06-30
I currently have a 9.04 install on a VPS server and have some questions about the best way to set permissions.  Let me explain my setup.

Each user will get their folder in /home and the default permissions are 750 and user:user so that only that user can see what is in their own folder and not be able to see any other user and won't even be able to list the files.

~/ is the users working directory and it will have /www/public_html in it.  This is not for [http://domain/~user](http://domain/~user) but instead will be for the user's fully qualified domain [http://domain/](http://domain/).

I ran into some permissions problems when setting up virtual hosts with apache2.  Even if I chown'ed /home/user/www/ to user:www-data I would get a permissions issue and we pages wouldn't display.  If I chmod'ed /home/user to 754/755 any web page would render fine with no permissions issues.

Is there a way I can keep each user's folder private from another but still allow them to host their domain in /home/user/www/?

---

