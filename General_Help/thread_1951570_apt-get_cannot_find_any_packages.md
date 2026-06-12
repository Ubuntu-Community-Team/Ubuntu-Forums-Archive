---
title: "apt-get cannot find any packages"
date: 2012-04-02
forum: General Help
---

### Post by iramusa on 2012-04-02
I have a freshly installed Ubuntu 9.04 and the apt-get is not particularly useful:

ira@ira-windu100:/etc/apt$ sudo apt-get install git.core
[sudo] password for ira: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package git.core
ira@ira-windu100:/etc/apt$ 

apt-get update/upgrade doesn't help in any way.

TIA

---

### Post by wojox on 2012-04-02
It should be git-core

May not work being 9.04 is no longer supported.

---

### Post by wildmanne39 on 2012-04-02
Hi, you can not install packages because that version of ubuntu is to old and the packages are no longer on the server.
Thanks

---

### Post by Bucky Ball on 2012-04-02
Go 10.04 LTS or wait for the next LTS release due late April, 12.04 LTS is my advice ... (Of course, the decision is yours ...) ;)

10.04 supported until April 2013 and is a simple upgrade via Update Manager to 12.04 when it is released. 12.04 LTS will have five years support rather than the regular LTS three years (a new innovation and good plan for mine). 

As mentioned, 9.04 reached EOL a while ago now.

---

### Post by iramusa on 2012-04-02
Thanks for help. Maybe while we're at it, could you recommend me a newer version that wouldn't be to 'heavy' for my MSI Wind u100 (Atom 1.6GHz) and that fits nicely on 10" screen?

---

### Post by wildmanne39 on 2012-04-02
Hi, I would install lubuntu.
Thanks

---

### Post by Bucky Ball on 2012-04-02
Xubuntu (xfce desktop environment, similar to Ubuntu's old Gnome) or Lubuntu (uses lightweight lxde desktop environment). There are many others lighter again (see Puppy Linux for one).

Be aware that newer versions of regular Ubuntu use the new Unity DE by default which you may or may not like ...

---

