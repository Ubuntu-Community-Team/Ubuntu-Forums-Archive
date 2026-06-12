---
title: "secvpn has some weird error on everything I install"
date: 2010-02-16
forum: General Help
---

### Post by billy314 on 2010-02-16
For a lot of the packages I install at the end it usually tells me some error about secvpn and that the package did not install completely.  But the wierd part is, everything I install works just fine despite that message.  I could copy/paste the exact message the next time I install a package if you want.  It seems like something I can just ignore but it sure is weird.

---

### Post by Satoru-san on 2010-02-16
Yes, please do give us some logs to work with. Otherwise we really can't tell you anything. :p

---

### Post by billy314 on 2010-02-16
here's an example:

```
Setting up secvpn (2.21+nmu1) ... 
Starting Monitor Daemon for Secure Virtual Private Network: cp: cannot stat `/etc/inittab': No such file or directory 
invoke-rc.d: initscript secvpnmon, action "start" failed. 
dpkg: error processing secvpn (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Errors were encountered while processing: 
 secvpn
```

---

