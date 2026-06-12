---
title: "Software installation fails everytime!"
date: 2011-05-23
forum: General Help
---

### Post by pd1108 on 2011-05-23
have a peculiar problem. using 11.04. Every time I install a program (any source - software center, Update manager ) at the end of the installation message it says operation failed.  But ... here is the big but.  The software gets installed.  Any idea what is happening?:confused:

---

### Post by Mr. Shannon on 2011-05-23
Try using **apt-get** to install something and see what error messages it gives you.  Note: Command line programs usually give better error messages.

Use the apt-get command like this:
```
sudo apt-get install package-name
```

---

### Post by pd1108 on 2011-05-24
Thanks for the tip.  It seems that the package crossplatformui is not installed properly and that is causing the problem.  Any Idea how to fix that - either remove or correct.

---

### Post by pd1108 on 2011-05-24
Yes it was that package.  managed to remove it thru synaptic and now package install and uninstall is working fine

---

