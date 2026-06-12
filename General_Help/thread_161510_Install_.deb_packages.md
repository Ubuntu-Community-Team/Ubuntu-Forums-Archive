---
title: "Install .deb packages"
date: 2006-04-17
forum: General Help
---

### Post by HereInOz on 2006-04-17
Hi All,

This has probably been asked before but I have done a few searches and found nothing, so here goes.

If I download a piece of software, in a .deb package, to my desktop, then run apt-get to install it, it tells me that it can't find the package.  My guess is that the sources.list file is being read, and the package, not being in the repositories listed in the sources.list file, is therefore not found.  

How can I tell apt-get that the file I am wanting to install is on my desktop, and not in the on-line repositories?

Is this possible, or am I trying to do something that is not do-able?  Is it a matter of putting the particular path in the sources.list file (tried a few alternatives but got nowhere) or is there something else that needs to be done?

So to recap - I need to install software from a .deb package, and this package resides on my desktop.  Any clues on how it is done?

I hope you can help

Kind regards,

Alan.

---

### Post by fng on 2006-04-17
```
dpkg -i package.deb
```

---

### Post by HereInOz on 2006-04-17
Thank you - much appreciated

---

### Post by xXx 0wn3d xXx on 2006-04-17
[QUOTE=HereInOz]Thank you - much appreciated[/QUOTE]
If you want to be able to double click and install a .deb follow [ this tutorial. ](http://ubuntuforums.org/showthread.php?t=114215&highlight=easy+double+click+install)

---

