---
title: "Changing Apache's wwwroot path"
date: 2006-05-22
forum: General Help
---

### Post by Dennis Pedrie on 2006-05-22
Currently, Apache uses **/var/www/** as it's web root. I want to change this to a different location, but I can't find what I need to edit in order to accomplish this.

Thank you.

---

### Post by Ensnared on 2006-05-22
To change it you need to edit the site in question. Apache on Ubuntu operates with a system where you set up your sites in separate files in the directory /etc/apache2/sites-available, and make symlinks to those files in the /etc/apache2/sites-enabled directory to, well, enable them :)

The default site, which is probably the one you're looking for, is configured in the file /etc/apache2/sites-available/default

Edit that file, and change the DocumentRoot directive (and any other references to /var/www/ in the file), and restart Apache.

---

