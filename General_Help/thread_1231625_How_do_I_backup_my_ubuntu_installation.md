---
title: "How do I backup my ubuntu installation?"
date: 2009-08-04
forum: General Help
---

### Post by ceilingcat on 2009-08-04
I have FINALLY got my ubuntu server working the way I want and now think it would be timely to back it up?  Apart from tarballing the whole contents of the hard drive, what would be a method to backup just the files i have installed?  It is obvious to backup /var/www/ but what other directories should I save, given that I use the default settings of packages installed by using apt-get?  cheers

---

### Post by approaching on 2009-08-04
rsync is an incremental file synchronization app that can work locally, or over a network. It will take a while the first time, but after that it is really quick. With what you are probably trying to do, run it via crontab.

---

### Post by ceilingcat on 2009-08-04
ok and thanks .. i will have a look at rsynch

---

