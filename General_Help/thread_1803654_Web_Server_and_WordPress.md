---
title: "Web Server and WordPress"
date: 2011-07-13
forum: General Help
---

### Post by nsathees on 2011-07-13
I have LAMP solution installed on Ubuntu 11.04

Very used to XAMPP under winXP which works flawlessly. But gave up windows due to other problems and choose Ubuntu.

I am very satisfied with Ubuntu except the LAMP.

I have a plug-in developed for WordPress and it works as it should in my Online server. But the localhost installation is not even detecting it. There is no PHP Error. (Yes I have turned the Error reporting on in php.ini and yes I have restarted Apache2)

Further more I have many folders under WWW folder which I access like [http://localhost/chariot/](http://localhost/chariot/)

but some WordPress installation works and some not. Some works some times and other time not.

Since the WordPress plug-in works fine online I know that plug-in is ok.

So what should I do next? I am a web developer and I need LAMP runs flawlessly that any thing else!

Appreciate your help!

---

### Post by Habitual on 2011-07-13
possible to edit /etc/hosts and add a 127.0.0.1 (or 192.x) for the "online" domain and have it resolve locally instead?

I know that WP LOVES resolvable domains over IP addresses.

Just a guess.

---

### Post by mikejonesey on 2011-07-13
can only guess as don't have logs but try checking the file permissions on one that works and one that does not...

---

