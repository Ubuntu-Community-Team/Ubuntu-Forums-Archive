---
title: "Directory trashed?"
date: 2010-12-24
forum: General Help
---

### Post by nimbusgb on 2010-12-24
It appears that on monday something trashed the apache2 config directories / files on a server I am running.

At first I thought it was a user that had gone in and deleted all the contents of the directories ( examining them with ssh ftp showed empty directories ) but this morning I'm digging around and things are getting curiouser and curiouser as Alice said.

as root cd /etc/apache2/sites-available results in a permission denied response - odd thinks me.

ls -la /etc/apache2/sites-available returns this  ....

ls: cannot access /etc/apache2/sites-available/.: Permission denied
ls: cannot access /etc/apache2/sites-available/default: Permission denied
ls: cannot access /etc/apache2/sites-available/default-ssl: Permission denied
ls: cannot access /etc/apache2/sites-available/..: Permission denied
total 0
d????????? ? ? ? ?                ? .
d????????? ? ? ? ?                ? ..
-????????? ? ? ? ?                ? default
-????????? ? ? ? ?                ? default-ssl

clearly something has run wild in the directory.

can anyone throw some light on this?

---

