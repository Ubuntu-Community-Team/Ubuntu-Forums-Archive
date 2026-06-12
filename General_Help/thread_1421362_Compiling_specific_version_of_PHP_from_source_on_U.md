---
title: "Compiling specific version of PHP from source on Ubuntu"
date: 2010-03-04
forum: General Help
---

### Post by kenny99 on 2010-03-04
Hi, I'm finding it difficult to find out the correct way to compile a specific version of PHP (5.1.6) from source. I have just bought a web server running Ubuntu and I need to install the LAMP stack with specific software versions as I need to mirror a production server I'm developing a website for. Should I be using wget to retrieve the versions i'm looking for and are there other important steps to consider? I've only used apt-get for local installations up until now.

Apologies if this is basic stuff, just want to make sure i do it correctly and struggled to find clear info via searching the forum/google.

---

### Post by kenny99 on 2010-03-04
Ok I intalled PHP 5.1.6 from source using wget and compiled it with Apache 2.2, tried a phpinfo() test which worked fine so all good so far. Annoyingly though, phpinfo() shows the PHP version as 5.2.1 (with JSON enabled), whereas running php-v in the shell shows as 5.1.6. Anyone any ideas what might be happening here? I need to make sure it is 5.1.6 which is installed.

---

