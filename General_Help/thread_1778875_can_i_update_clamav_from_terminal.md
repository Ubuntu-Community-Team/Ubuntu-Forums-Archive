---
title: "can i update clamav from terminal?"
date: 2011-06-09
forum: General Help
---

### Post by cthom on 2011-06-09
i get a notice to upgrade from 0.97 to 0.97.1 clamav. can i do this from terminal? what command do i use to update?

---

### Post by TeoBigusGeekus on 2011-06-09
Try 
```
sudo apt-get update
sudo apt-get install clamav
```

---

### Post by linuxinstalledfromhdd on 2011-06-09
Unfortunately you can't update those components of clamav that way.  The repo is slighty behind the actual release 'source' version.. directly from their web site.

You can however remove ClamAv and compile it yourself so you will have the latest version of everything.. 

[http://volatile-minds.blogspot.com/2008/06/installing-clamav-latest-from-source.html](http://volatile-minds.blogspot.com/2008/06/installing-clamav-latest-from-source.html)

I use BitDefender since it has resident scanner and autostart into tray features.. 

Try it:

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

Look for Bitdefender on that list, and you can install the bittorrent repository in synaptic package manager.  The key is free.

---

### Post by cthom on 2011-06-10
ah, i suspected as much. since i'm not really a 'compile person' ( :oops: ) i'll try the bitdefender. ta :)

---

