---
title: "newbie needs help with dpkg on oneiric"
date: 2011-11-02
forum: General Help
---

### Post by xr4ti on 2011-11-02
i am running this command on oneiric:
 
```
dpkg -i virtualbox-4.1_4.1.4-74291~Ubuntu~oneiric_i386.deb
```
 
can someone tell me what the error output (below) means and how to fix it? 
 
```
dpkg: dependency problems prevent configuration of virtualbox-4.1:i386:
 virtualbox-4.1:i386 depends on libpython2.7 (>= 2.7).
 virtualbox-4.1:i386 depends on libxml2 (>= 2.7.4).
 virtualbox-4.1:i386 depends on libxmu6.
 virtualbox-4.1:i386 depends on psmisc.
 virtualbox-4.1:i386 depends on adduser.
dpkg: error processing virtualbox-4.1:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 virtualbox-4.1:i386
```

---

### Post by Script Warlock on 2011-11-02
sudo apt-get -f install

---

### Post by hailtothethief on 2011-11-02
I don't think your deps are broken, I think you're just lacking the right ones. Run 

```
sudo apt-get install libpython2.7 libxml2 libxmu6 psmisc adduser
```

and try again. Good luck!

---

