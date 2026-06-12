---
title: "Install MongoDB 2.0.0 - Synaptic Error?"
date: 2011-10-05
forum: General Help
---

### Post by Gias Kay on 2011-10-05
Hello everyone,

I am trying to install MongoDB 2.0.0 following this official guide:

[COLOR="RoyalBlue"][http://www.mongodb.org/display/DOCS/Ubuntu+and+Debian+packages](http://www.mongodb.org/display/DOCS/Ubuntu+and+Debian+packages)[/COLOR]

After I completed the setup, there will be some error every time I check for upgrades with apt-get/Synaptic. I was under the impression that the setup failed before I manually checked the package and discovered that it indeed was showing the latest version (v2.0.0) instead of the one coming with Maverick (v1.4.4).

Anyone has any idea on how to get rid of the error? Will it affect the actual install? Thanks!

---

### Post by Gias Kay on 2011-10-05
Sorry, link fixed.

---

### Post by Gias Kay on 2011-10-06
*bump*

Anyone?

---

### Post by arkham on 2012-03-06
Can you post the actual error you are getting?

My immediate suspicion would be that you might have skipped adding the gpg key:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 7F0CEB10
```

A.

---

