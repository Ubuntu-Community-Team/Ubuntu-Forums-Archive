---
title: "Help: How to encrypt ~/ for all user"
date: 2011-04-11
forum: General Help
---

### Post by ubuntu27 on 2011-04-11
Ubuntu Natty is release date is coming, so I figure it is the right time to ask this.

So, I have been using ecryptfs since Ubuntu 10.10. and I like it.
However, when I setup ecryptfs in Ubuntu with the DesktopCD upon OS installation, it only encrypts the _first user_, namely the one with sudo abilities. 

How do I encrypt every home directory?

---

### Post by bodhi.zazen on 2011-04-11
Use the command line :

```
sudo adduser --encrypt-home user_to_add
```

See also the man pages.

[http://manpages.ubuntu.com/manpages/natty/en/man8/adduser.8.html](http://manpages.ubuntu.com/manpages/natty/en/man8/adduser.8.html)

---

