---
title: "errors while processing samba, samba-common"
date: 2009-10-04
forum: General Help
---

### Post by meluzi02 on 2009-10-04
i have run the command:

       **sudo dpkg --configure -a** 

and got this result:

[B]Setting up samba-common (2:3.3.2-1ubuntu3.2) ...
dpkg: error processing samba-common (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of samba:
 samba depends on samba-common (= 2:3.3.2-1ubuntu3.2); however:
  Package samba-common is not configured yet.
dpkg: error processing samba (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 samba-common
 samba[/B]

what are the possible errors in samba and samba-common?

---

### Post by gradysghost on 2009-10-29
I'm having the same exact problem.  Are you running Karmic (final release) like I am?  I would really love to set up my shares already.

---

### Post by gradysghost on 2009-10-29
Okay, instead of using apt-get, use aptitude.

```
sudo aptitude install samba
```

The problem (in my specific case) is that samba-common in the Karmic repos is a newer version than what samba depends on.  samba-common needs to be downgraded, and aptitude will do this.  I've managed to get the install running, and I'll see if it actually ends up working in a few minutes.

---

