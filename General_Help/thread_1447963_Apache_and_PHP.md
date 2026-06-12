---
title: "Apache and PHP"
date: 2010-04-06
forum: General Help
---

### Post by WASasquatch on 2010-04-06
So, I installed Apache, and PHP5, MySQL, and so on, their latest builds. All the good stuff. Anyways... can someone point out where this was installed!? Lol [http://localhost/](http://localhost/) says it works for me, so, that's great. Just need the location. Lol.

---

### Post by SnickerSnack on 2010-04-06
I've done this recently, but I didn't quite remember where it was located.  So, I tried this:

$ sudo updatedb
$ locate html | grep default

One of the results (near the end of the list) was:

/usr/share/apache2/default-site/index.html

bingo.

It should be possible to change where apache looks for your site, but I don't remember if I figured that out.  I haven't had to use apache yet.

Edit: Hmmm, now I'm starting to think that it's here:

/etc/apache2/sites-available/

and I seem to remember having mine working, though now I get a 403 error.  The permissions look fine to me.

Edit: OR, it could be /var/www/index.html

---

### Post by mcduck on 2010-04-06
> **WASasquatch said:**
> So, I installed Apache, and PHP5, MySQL, and so on, their latest builds. All the good stuff. Anyways... can someone point out where this was installed!? Lol [http://localhost/](http://localhost/) says it works for me, so, that's great. Just need the location. Lol.

Just like any other Linux app, it was installed all around the system, each file in the same place with other files with similar purposes.

Anyway, the default WWW root directory is /var/www, and you'll find the configuration files in /etc/apache2.

---

