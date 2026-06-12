---
title: "LAMP server only displays pages with exact path, folder gives Forbidden"
date: 2009-11-10
forum: General Help
---

### Post by paulhurleyuk on 2009-11-10
I'm instally a new PC to be my home server, currently it's installed with MythBuntu 9.10 and I'm in the process of installing Mediawiki.

If I try to access mediawiki via just the folder (i.e [http://localhost/mediawiki](http://localhost/mediawiki)) I get a Forbidden You don't have permission to access /mediawiki/ on this server.  If I try the full path (i.e [http://localhost/mediawiki/index.php](http://localhost/mediawiki/index.php)) I get the correct page.

I assume this is because myth (or more specificaly mythweb) has put some funky options in /etc/apache2/apache.conf or another config file, but nothing springs to mind.

Does anyone have any ideas of which setting needs tweaking so apache delivers the index.php file for the folder (of a folder listing)

Thanks

Paul

---

### Post by oraknabo on 2009-11-10
Make sure httpd.conf allows php pages as default files.

---

### Post by paulhurleyuk on 2009-11-10
It was mythbuntu's setup for Mythweb that was screwing things up.  I Edited /etc/apache2/sites-enabled/default-mythbuntu, and right near the top commented out the “DirectoryIndex mythweb” line.  restart apache and bingo - all works as it should

Thanks

Paul.

---

