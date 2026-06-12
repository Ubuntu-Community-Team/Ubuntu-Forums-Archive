---
title: "Newest midori package won't install from repos."
date: 2009-08-12
forum: General Help
---

### Post by codyxx on 2009-08-12
I get this error when running sudo apt-get install midori for version 0.1.9:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  midori: Depends: libsoup2.4-1 (>= 2.27.2) but 2.26.0-0ubuntu3 is to be installed
          Depends: libwebkit-1.0-2 (>= 1.1.6) but it is not installable
E: Broken packages

```

---

### Post by codyxx on 2009-08-13
Bump

---

### Post by arky on 2009-08-13
Make sure you computer is uptodate. 

sudo apt-get update 
sudo apt-get dist-upgrade
sudo apt-get install midori 

If the broken packages problem persists, report a bug

---

### Post by ad_267 on 2009-08-13
You need to add the webkit ppa: [https://launchpad.net/~webkit-team/+archive/ppa](https://launchpad.net/~webkit-team/+archive/ppa)

It says that on the Midori ppa page.

---

### Post by hetx on 2009-08-13
Make sure you have the webkit PPA for Midori too.

```
deb http://ppa.launchpad.net/webkit-team/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/webkit-team/ppa/ubuntu jaunty main
```

I updated today, worked fine.

---

