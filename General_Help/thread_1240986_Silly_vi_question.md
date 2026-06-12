---
title: "Silly vi question"
date: 2009-08-15
forum: General Help
---

### Post by Terryg80 on 2009-08-15
I'm trying to setup a file server using the how to here: [http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver)


Everything went smooth until I got to the part where I edit the network settings.  I log in with putty, get in su mode, and type vi /etc/network/interfaces  The config file opens, I make the appropriate changes, and try to save and quit but nothing happens.  I'm under the impression that typing :q saves and quits, and it works fine as long as I don't make any edits, but if I change one thing in the file I can't get it to close.


I'm sure it's something simple that I'm just not getting, so be gentle.  Any help would be greatly appreciated.

Thanks

---

### Post by michy99 on 2009-08-15
To save changes and quit :wq. You may want to try nano instead of vi. I find it much easier.

---

