---
title: "Easiest upgrade from 5.04 to 5.10"
date: 2006-04-30
forum: General Help
---

### Post by Lomz on 2006-04-30
What is the easiest way to upgrade from ubuntu 5.04 to 5.10?
without formating?

---

### Post by jrib on 2006-04-30
[quote=Lomz]What is the easiest way to upgrade from ubuntu 5.04 to 5.10?
without formating?[/quote] 
Hey Lomz, there is a pretty easy to follow guide on 
[http://wiki.ubuntu.com/BreezyUpgrade]("http://wiki.ubuntu.com/BreezyUpgrade") .  If you have a broadband connection, easiest way is to just follow the directions for using apt by modifying sources.list and then using apt-get dist-upgrade .  If you have any questions about it, just ask

---

### Post by r4ik on 2006-04-30
Replace all  Hoary with Breezy in your  "sudo gedit  /etc/apt/sources.list" and save it.

sudo apt-get update

sudo apt-get dist-upgrade

Enjoy and Good luck !

---

