---
title: "Cinelerra update + upgrade message!"
date: 2009-12-05
forum: General Help
---

### Post by Rytron on 2009-12-05
Hello.

Anytime I run sudo apt-get update; sudo apt-get upgrade

I get this message at the end in my terminal:

Setting up cinelerracv (2.1.1-git091001akirad2) ...
cannot open locale definition file `de_DE': No such file or directory
dpkg: error processing cinelerracv (--configure):
 subprocess installed post-installation script returned error exit status 4
Errors were encountered while processing:
 cinelerracv
E: Sub-process /usr/bin/dpkg returned an error code (1)

I installed Cinelerra from here: [http://cinelerra.org/getting_cinelerra.php#ubuntu](http://cinelerra.org/getting_cinelerra.php#ubuntu)

How do I sort this out?

Note: When I do sudo apt-get update I don't get the above message.
Note: Cinelerra works fine.

---

### Post by Rytron on 2010-01-24
Delete all passages relating to Cinelerra.
```
sudo gedit /var/lib/dpkg/status
```

---

### Post by RubenK on 2010-03-16
Did you do anything after this? Still not working here...

---

### Post by Rytron on 2010-03-17
That is all I did. Consider using Cinecutie [http://akiradproject.net/cinecutie]("http://akiradproject.net/cinecutie")

Hope this helps you.

---

### Post by RubenK on 2010-03-17
Cinecutie works fine. Thanks!

---

### Post by Rytron on 2010-03-17
> **RubenK said:**
> Cinecutie works fine. Thanks!

Excellent. Glad to help. ;)

---

