---
title: "LAMPP Referencing Wrong Document Root Folder"
date: 2009-09-04
forum: General Help
---

### Post by iEthan on 2009-09-04
Nevermind. I have resolved the issues.

I had installed CakePHP command-line and it had installed apache2-common, and overrided the LAMPP. Oops.

[s]So, I have LAMPP (XAMPP) installing on my install in /opt/lampp/. The web directory is at /opt/lampp/htdocs/.

All was working fine for a while, but when I rebooted today and started up LAMPP, and pointed my browser to [http://localhost/](http://localhost/), and instead of referencing /opt/lampp/htdocs/ as the document root, it references /var/www/.

I thought Apache (or Apache 2) might be installed. I did the apt-get purge command and it isn't installed.

What is the problem here?

**Update:** I ran the following command:
```
sudo /opt/lampp/lampp startapache
```
and got the following results:
```
XAMPP: Another web server daemon is already running.
```

I also have LiteSpeed installed, but I stopped it. And besides, the document root is /opt/lsws/DEFAULT/html/.[/s]

---

