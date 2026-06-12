---
title: "Can't login in my Ubuntu"
date: 2012-09-12
forum: General Help
---

### Post by bsa795 on 2012-09-12
First I installed Python2.7 successfully (from tarball), and soon after that Synaptic package manager started throwing some errors about package system being corrupted...

Synaptic recommended running ```
sudo apt-get install -f
``` which I did... Than I restarted and I cannot login anymore! I enter my password but when I try to login I'm redirected to login page again...
While apt-get install was running I noticed it said that some disk space will be **freed ** - it seems it removed some of the vital components. How is it possible that something system recommended itself (running this command) makes it unusable > that's pretty bad.

Ubuntu version is 10.04... Is there any way of repairing this installation? (When I use Ctrl+Alt+F1 I can login, is it possible to repair it from there)?

---

### Post by Ubunterrific on 2012-09-12
> **bsa795 said:**
> First I installed Python2.7 successfully (from tarball), and soon after that Synaptic package manager started throwing some errors about package system being corrupted...

Synaptic recommended running ```
sudo apt-get install -f
``` which I did... Than I restarted and I cannot login anymore! I enter my password but when I try to login I'm redirected to login page again...
While apt-get install was running I noticed it said that some disk space will be **freed ** - it seems it removed some of the vital components. How is it possible that something system recommended itself (running this command) makes it unusable > that's pretty bad.

Ubuntu version is 10.04... Is there any way of repairing this installation? (When I use Ctrl+Alt+F1 I can login, is it possible to repair it from there)?

Yep, if you log in via a virtual terminal (ctrl + alt + f1), you can do sudo apt-get stuff.
If you can't remember what it was specifically you pulled out (lightdm?) (unity-greeter?), you could always do:
```
 sudo apt-get install --reinstall ubuntu-desktop
```
which will pull back all the default packages like when you first installed ubuntu. It's better than nothing, but there are of course many other options. 
I can't understand why you installed python 2.7 from a tarball - isn't 2.7.3 in the repositories as a nice .deb?

---

### Post by bsa795 on 2012-09-13
Thanks for you suggestion, but unfortunately this isn't helping, I got this message:
```
E: Broken packages
```

Here's what I get just after running this command...

[IMG]http://i47.tinypic.com/9zrqc7.png[/IMG]

As for Python from tarball - Synaptic installed an older version of python and I needed 2.7 - that's why I tried from tarball and was not aware of this 2.7.3 .deb unfortunately!

Just to mention this - after installing Python the only other command I ran was this one for an attempt to install Mercurial, this one: (from Mercurial folder)
```
sudo make install PYTHON=/usr/local/src/Python-2.7.3 PREFIX=/opt
```

I tried to install some of these packages ubuntu-desktop depends on, and I can't install any of them. I always get 'E: Broken packages' error. OMG why did the system recommend running '...install -f' when this ruined my system?

Is there any other way to salvage this Ubuntu? Any other way to sort of 'repair' all these packages and dependencies?

---

### Post by sid0972 on 2012-09-13
you can boot from recovery mode, build the broken packages again, and try booting again

---

