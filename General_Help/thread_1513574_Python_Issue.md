---
title: "Python Issue"
date: 2010-06-19
forum: General Help
---

### Post by Akira_Oni on 2010-06-19
A while ago, I had an issue with ubuntu becoming inaccessible to me. Here's a link to the thread:

[http://ubuntuforums.org/showthread.php?t=1486399](http://ubuntuforums.org/showthread.php?t=1486399)

Since then I've been able to recover my os, and most everything works, but I've been having major issues with python. Every time I try to install something, python kills it. It had been preventing me from opening open-office as well. Here was the original error I received.

```
E: /var/cache/apt/archives/libanyevent-perl_5.240-1_all.deb: trying to overwrite '/usr/share/man/man3/AnyEvent.3pm.gz', which is also in package anyevent-perl 
```

I recently tried reinstalling python from the synaptic package manager. Here was the error I recieved.

```
E: python-lazr.uri: subprocess installed post-installation script returned error exit status 2
E: python-wadllib: dependency problems - leaving unconfigured
E: python-lazr.restfulclient: dependency problems - leaving unconfigured
E: python-launchpadlib: dependency problems - leaving unconfigured
E: python-apport: dependency problems - leaving unconfigured
E: apport: dependency problems - leaving unconfigured
E: apport-gtk: dependency problems - leaving unconfigured
E: ubuntuone-client: dependency problems - leaving unconfigured
E: ubuntuone-client-gnome: dependency problems - leaving unconfigured

```

I got the same message when I tried to reinstall perl. Any suggestions?

---

