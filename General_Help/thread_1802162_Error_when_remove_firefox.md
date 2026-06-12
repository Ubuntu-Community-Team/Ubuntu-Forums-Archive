---
title: "Error when remove firefox"
date: 2011-07-11
forum: General Help
---

### Post by kswix on 2011-07-11
Hi!

When I try to remove firefox in software center, I see something like this:
```
installArchives() failed: (   ...  (   ... 5% (   ... 10% (   ... 15% (   ... 20% (   ... 25% (   ... 30% (   ... 35% (   ... 40% (   ... 45% (   ... 50% (   ... 55% (   ... 60% (   ... 65% (   ... 70% (   ... 75% (   ... 80% (   ... 85% (   ... 90% (   ... 95% (   ... 100% (   ...     154746   .) 
  firefox ... 
update-alternatives: : /var/lib/dpkg/alternatives/gnome-www-browser :   
dpkg:     firefox (--remove): 
    pre-removal    2 
No apport report written because MaxReports is reached already
Please restart all running instances of firefox, or you will experience problems. 
     : 
 firefox
```When I try sudo apt-get install -f, I see this:
```
chromium-browser
 epiphany-browser
 firefox
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by fdrake on 2011-07-11
what about

```
sudo apt-get purge firefox
```?

---

### Post by kswix on 2011-07-25
I'm working with packages and get this error:
```
installArchives() failed: (   ... 
(   ... 5%
(   ... 10%
(   ... 15%
(   ... 20%
(   ... 25%
(   ... 30%
(   ... 35%
(   ... 40%
(   ... 45%
(   ... 50%
(   ... 55%
(   ... 60%
(   ... 65%
(   ... 70%
(   ... 75%
(   ... 80%
(   ... 85%
(   ... 90%
(   ... 95%
(   ... 100%
(   ...     179737   .)
  firefox ...
update-alternatives: : /var/lib/dpkg/alternatives/gnome-www-browser :  
dpkg:     firefox (--remove):
    pre-removal    2
No apport report written because MaxReports is reached already
Please restart all running instances of firefox, or you will experience problems.
     :
 firefox
```
What I must do?

---

### Post by kswix on 2011-08-09
So, I solve problem with deleting browsers, but now I have another trouble:

Synaptic and Ubuntu Software Center shows that's browsers are deleted, but I see them in Applications -> Internet and I can open them, and they works! What I must do?

---

