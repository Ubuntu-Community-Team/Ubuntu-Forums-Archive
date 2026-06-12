---
title: "Unable to install Pidgin"
date: 2011-01-02
forum: General Help
---

### Post by iNsOmNiOuS on 2011-01-02
Hey guys... When trying to install pidgin from repos, and many other apps. It fails giving messages a bit like this :

```
root@ubuntu:~# apt-get install pidgin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgconf2-4: Depends: gconf2-common (>= 2.28) but it is not going to be installed
               Depends: gconf2-common (< 2.29) but it is not going to be installed
  pidgin: Depends: libice6 (>= 1:1.0.0) but it is not going to be installed
          Depends: libpurple0 (>= 1:2.6.0) but it is not going to be installed
          Depends: libsm6 but it is not going to be installed
          Depends: libstartup-notification0 (>= 0.10) but it is not going to be installed
          Depends: libxss1 but it is not going to be installed
          Depends: gconf2 (>= 2.10.1-2) but it is not going to be installed
          Recommends: gstreamer0.10-plugins-good but it is not going to be installed
E: Broken packages
```Any ideas on how to fix ?

---

### Post by LetsMugSanta on 2011-01-02
Have you tried just downloading from the website?

---

### Post by iNsOmNiOuS on 2011-01-02
Already tried that. They offer a PPA, Which is unable to be installed because Pidgin can't be installed...

[IMG]http://www.freeimagehosting.net/uploads/6f70b890ea.png[/IMG]

---

### Post by cgroza on 2011-01-02
Try this:

```
sudo apt-get update
sudo apt-get -f install
sudo dpkg --configure -a --force-all
```

---

