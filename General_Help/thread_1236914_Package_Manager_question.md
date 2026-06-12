---
title: "Package Manager question"
date: 2009-08-10
forum: General Help
---

### Post by aspiringbum on 2009-08-10
Hello all,

I am running Xubuntu on a Acer Aspire One netbook.  I am having a consistent error with the Synaptic package manager every time it launches.  When I run the update I get an error, and I have posted a picture below of the error.  Thanks!

[IMG]http://i11.photobucket.com/albums/a198/bobbaloo78/erroroccured.png[/IMG]

---

### Post by michy99 on 2009-08-10
Run this command in a terminal:```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9
```

---

### Post by TheForumTroll on 2009-08-10
When you add a ppa you need to import the key it lists on the page if you don't want to see the error.

[Have a look here]("https://help.launchpad.net/Packaging/PPA/InstallingSoftware").

---

### Post by aspiringbum on 2009-08-10
Wow! thanks for the speedy replies guys!  Michy99, your command worked like a charm! thanks!

---

