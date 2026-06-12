---
title: "Dreamweaver and unbutu"
date: 2010-05-11
forum: General Help
---

### Post by surajrasaq on 2010-05-11
hii, pls can anybody help me? i recently moved from windows platform to linus, i install dream weaver successfully using wine and also i was able to get my apache, php, and mysql working. but the problem is i can not display the site i built on the server, is there anyway i can get my files to work on the server? the problem seem to be how to get the server to recognize files i built with dreamweaver, if i can get this done my Microsoft days are over.
thanx

---

### Post by Orange Kingdom on 2010-05-11
Put the html files in the /var/www directory (root of the apache server) and point your webbrowser to localhost.

---

### Post by surajrasaq on 2010-05-12
> **Orange Kingdom said:**
> Put the html files in the /var/www directory (root of the apache server) and point your webbrowser to localhost.
thank you, but i still another problem, i don't have the privilege to copy files to this folder, how do i get this privilege?

---

### Post by darolu on 2010-05-12
Use "sudo":
```
$ sudo cp /home/<user>/yourfiles /var/www
```
You can also change the virtualhost directory by editing:
```
$ gksudo gedit /etc/apache2/sites-available/default
```
BTW; why don't try a native Linux application? Quanta is quite similar to Dreamweaver:
```
$ sudo apt-get install quanta
```

---

