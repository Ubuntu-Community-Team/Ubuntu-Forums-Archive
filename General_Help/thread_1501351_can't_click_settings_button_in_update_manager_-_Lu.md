---
title: "can't click settings button in update manager - Lucid"
date: 2010-06-04
forum: General Help
---

### Post by rbjscv on 2010-06-04
I did a fresh install of Lucid about 3 weeks ago.  At time I used the Update Manager & selected the best download location for my area.

No the Settings button is grayed out and I am no longer able to make changes in Update Manager.  Rebooting is of no help. I've looked for an option to change in the Configuration editor but see nothing.

How do I get my settings button to work again please?

---

### Post by philinux on 2010-06-04
What happens if you try to open system>admin>software sources or in synaptic

settings>repositories? Both of which are the same thing as settings in update manager.

Also post the output of:- ```
cat /etc/apt/sources.list
```

---

### Post by rbjscv on 2010-06-04
In Synaptic the repositories show. 

Don't have this option available:  system>admin>software sources

output of /etc/apt/sources.list

```
 ## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://ubuntu.media.mit.edu/ubuntu/ lucid-security main restricted
deb-src http://ubuntu.media.mit.edu/ubuntu/ lucid-security main restricted
deb http://ubuntu.media.mit.edu/ubuntu/ lucid-security universe
deb-src http://ubuntu.media.mit.edu/ubuntu/ lucid-security universe
deb http://ubuntu.media.mit.edu/ubuntu/ lucid-security multiverse
deb-src http://ubuntu.media.mit.edu/ubuntu/ lucid-security multiverse
deb http://ppa.launchpad.net/ssakar/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/ssakar/ppa/ubuntu lucid main
deb http://archive.getdeb.net/ubuntu karmic-getdeb apps
 
```

would a screen shot help?

Thank you for your help.  I must be over-looking something. but I can't imagine. I've been using Ubuntu for 3 years now so I mostly know what I'm doing - until now.

---

### Post by philinux on 2010-06-04
So this is an upgrade not a clean install?

If everthing is working i would use Synaptic to change the software sources as the settings button in update manager goes to the same thing. Which is software-properties-gtk.

Try running it from a terminal.

```
gksu software-properties-gtk

```

---

### Post by rbjscv on 2010-06-04
It was a clean install. And I know I selected the best site to download from.

I don't see an option in Synaptic repositories to change the download site. I thought there was.

gksu software-properties-gtk   Running this didn't do anything that I can see.  What am I looking for?

---

### Post by rbjscv on 2010-06-04
Solved!

Opened Synaptic, looked in Not installed (residual conf) and found software-properties-gtk.  Reinstalled it and now all is fixed.

Thanks for suggesting software-properties-gtk.  That jogged my mind and made me look to see if it was even installed.  
Thanks you for you help this morning.

---

