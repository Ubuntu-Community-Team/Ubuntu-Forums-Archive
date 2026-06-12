---
title: "could not mark all packages for installation"
date: 2009-11-13
forum: General Help
---

### Post by theneoindian on 2009-11-13
when i use synaptic to install some packages , i get this error :

"could not mark all packages for installation ". i've given below the full error i got when tryin to install minitube :

```

the following packages have unresolved dependencies . make sure all rew dependencies are enabled in the preferences
minitube:
  Depends: libqt4-network (>=4.5.1) but 4.5.0-0ubuntu4.2 is to be installed
 Depends: libqt4-phonon (>=4.5.1) but it is not installable
  Depends: libqt4-xml (>=4.5.1) but 4.5.0-0ubuntu4.2 is to be installed
  Depends: libqtcore4 (>=4.5.1) but 4.5.0-0ubuntu4.2 is to be installed
  Depends: libqtgui4 (>=4.5.1) but 4.5.0-0ubuntu4.2 is to be installed


```

---

### Post by bashphoenux on 2009-11-13
you need to go to synpatic and install the above mentioned library files first before  trying to install the package you want !!! :)

---

### Post by peasead on 2009-11-21
> when i use synaptic to install some packages , i get this error :

"could not mark all packages for installation ". i've given below the full error i got when tryin to install minitube :I'm having the same issue...when I try to update to more current versions, I'm told that I have the most current version. 

You have x64 don't you? Me thinks you probably do...the only way you can get 4.5.1 are "experimental" libraries and then a lot of other things will stop working that require 4.5.0 (Skype etc).

---

