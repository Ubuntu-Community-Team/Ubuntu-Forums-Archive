---
title: "Apache2 doesn't load the site at startup"
date: 2009-07-13
forum: General Help
---

### Post by stef2n on 2009-07-13
Hi, everybody!

I have installed Ubuntu 9.04 on my laptop. Also I have installed apache2 and configured a site on localhost. The site is okay, I had installed it before in the same configuration on my PC. When I start Ubuntu and try to access the site, I get the 403 error (Forbidden access). If I restart apache, everything works well till the next reboot. What can I do to solve this?

Any help will be appreciated. Thank you!

---

### Post by utnubuuser on 2009-07-13
Do you own the /www folder?

> sudo chown -R yourusername /var/www

---

### Post by stef2n on 2009-07-13
I wasn't the owner. Now I am and the problem persists.

---

