---
title: "Cannot install python-xpcom"
date: 2009-08-23
forum: General Help
---

### Post by Wiiboy on 2009-08-23
Hi guys,
I'm trying to install python-xpcom on Karmic alpha 4 (because I love alphas :P).
```

wiiboy@wiiboy-laptop:~$ sudo apt-get install python-xpcom
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  python-xpcom: Depends: python (< 2.6) but 2.6.2-0ubuntu1 is to be installed
E: Broken packages

```

What's the problem?  And can I fix it?

---

### Post by karthick87 on 2009-08-23
Try..
sudo apt-get clean all
sudo apt-get -f install
sudo apt-get update

---

### Post by Wiiboy on 2009-08-23
Nope.  It still gives the same error.

I've got 180 updates to do, because I just install Karmic.  Should I do those now?

---

