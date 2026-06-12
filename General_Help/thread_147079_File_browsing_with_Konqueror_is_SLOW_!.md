---
title: "File browsing with Konqueror is SLOW !"
date: 2006-03-19
forum: General Help
---

### Post by skaboss on 2006-03-19
Hello,

For several days now, i noticed that Konqueror is really slow when browsing file system. Does someone have any clue, please ?

---

### Post by Barrakketh on 2006-03-19
Disable previews.  They bog it down a lot.  If you have a large amount of files (and I do mean large) in a single directory you may be better off using an ODM like [Krusader](http://krusader.sf.net).

Also, there seems to be a process that both Konqueror and GNOME use to watch files for updates, but it has the nasty side effect of randomly hogging CPU/RAM when you rapidly update a *lot*.  The process is called gam_server, and you can give it a "killall gam_server".  It'll relaunch and now be less bloated.

---

### Post by skaboss on 2006-03-20
Thanks a lot !
It seems like gam_server is guilty for this trouble : 
```
killall gam_server
``` solves my problem everytime i get it.

---

