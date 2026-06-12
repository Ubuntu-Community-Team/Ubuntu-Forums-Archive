---
title: "apt broken"
date: 2010-09-26
forum: General Help
---

### Post by tekromancr on 2010-09-26
I cant install anything using apt-get, aptitude, synaptic, or the ubuntu store :(
I keep getting the same error:
```
Errors were encountered while processing: 
 chromium-browser 
 firefox 
 firefox-gnome-support 
Setting up firefox (3.6.10+build1+nobinonly-0ubuntu0.10.04.1) ... 
update-alternatives: error: /var/lib/dpkg/alternatives/x-www-browser corrupt: invalid status 
dpkg: error processing firefox (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of firefox-gnome-support: 
 firefox-gnome-support depends on firefox (= 3.6.10+build1+nobinonly-0ubuntu0.10.04.1); however: 
  Package firefox is not configured yet. 
dpkg: error processing firefox-gnome-support (--configure): 
 dependency problems - leaving unconfigured
```Any ideas? :confused:

---

### Post by elliotn on 2010-09-26
sudo apt-get update

---

### Post by tekromancr on 2010-09-27
nope, tried that.

---

### Post by amauk on 2010-09-27
try
```
sudo apt-get install -f
```

---

### Post by tekromancr on 2010-09-29
Nope...
```
ggriffin@diaspara:~$ sudo apt-get install -f
[sudo] password for ggriffin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 22 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up chromium-browser (6.0.472.53~r57914-0ubuntu0.10.04.1) ...
update-alternatives: error: /var/lib/dpkg/alternatives/x-www-browser corrupt: invalid status
dpkg: error processing chromium-browser (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up firefox (3.6.10+build1+nobinonly-0ubuntu0.10.04.1) ...
update-alternatives: error: /var/lib/dpkg/alternatives/x-www-browser corrupt: invalid status
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox (= 3.6.10+build1+nobinonly-0ubuntu0.10.04.1); however:
  Package firefox is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 chromium-browser
 firefox
 firefox-gnome-support
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

