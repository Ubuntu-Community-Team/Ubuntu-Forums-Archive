---
title: "Accessing a shared drive in Ubuntu"
date: 2011-02-24
forum: General Help
---

### Post by hojjat on 2011-02-24
There is a shared drive (on a Samba server using Solaris, I guess) on a machine in our network. In windows, in order to access it I had to map the network drive by providing it's URI ([http://blah.domain.com/dir1](http://blah.domain.com/dir1)) and a username and password. How do I achieve the same thing in Ubuntu? While a terminal based solution is all I need, a graphical solution is much more appreciated.

---

### Post by seawolf167 on 2011-02-24
Try:

Places -> Connect to Server -> Enter the required username/share type/etc

Or using samba, you can open a folder and in the address bar type:

```
smb://ip.address.of.remote.machine
```

---

