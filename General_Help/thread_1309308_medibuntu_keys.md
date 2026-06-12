---
title: "medibuntu keys?"
date: 2009-11-01
forum: General Help
---

### Post by bryncoles on 2009-11-01
I am having trouble installing Medibuntu in Karmic. when i paste:

```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update
```

In the terminal, I get the following error message:

> --2009-11-01 12:49:49--  [http://www.medibuntu.org/sources.list.d/karmic.list](http://www.medibuntu.org/sources.list.d/karmic.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://wwwcache3.lancs.ac.uk/caching/unconfigured/?http%3A%2F%2Fwww.medibuntu.org%2Fsources.list.d%2Fkarmic.list](http://wwwcache3.lancs.ac.uk/caching/unconfigured/?http%3A%2F%2Fwww.medibuntu.org%2Fsources.list.d%2Fkarmic.list) [following]
--2009-11-01 12:49:49--  [http://wwwcache3.lancs.ac.uk/caching/unconfigured/?http%3A%2F%2Fwww.medibuntu.org%2Fsources.list.d%2Fkarmic.list](http://wwwcache3.lancs.ac.uk/caching/unconfigured/?http%3A%2F%2Fwww.medibuntu.org%2Fsources.list.d%2Fkarmic.list)
Resolving wwwcache3.lancs.ac.uk... 194.80.32.11
Connecting to wwwcache3.lancs.ac.uk|194.80.32.11|:80... connected.
HTTP request sent, awaiting response... 409 Conflict
2009-11-01 12:49:49 ERROR 409: Conflict.

Anyone know what the problem is?

*edit*

Oh yeah, I'm running the 64 bit install.

---

### Post by realzippy on 2009-11-01
edit: wrong answer

---

### Post by howefield on 2009-11-01
If your having trouble getting hte key with the server being down, try using one of these alternatives.

[http://pgp.mit.edu/](http://pgp.mit.edu/)
keyserver.pgp.com

---

### Post by bryncoles on 2009-11-01
> **howefield said:**
> If your having trouble getting hte key with the server being down, try using one of these alternatives.

[http://pgp.mit.edu/](http://pgp.mit.edu/)
keyserver.pgp.com

Is the server down then? And what do I do with that link you posted (yes, I click it and it takes me to a new website - but this new website just confuses me...)

---

### Post by howefield on 2009-11-01
> **bryncoles said:**
> And what do I do with that link you posted (yes, I click it and it takes me to a new website - but this new website just confuses me...)

Type medibuntu in the search field, press enter and you will see links to the "Launchpad PPA for Medibuntu Packaging Team"

Clicking on the link will lead you to the key which you can copy/paste into a text file for importing into synaptic package manager.

[http://www.debianadmin.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html](http://www.debianadmin.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html)

Another option is to download the .deb packages from the medibuntu website. Most users I guess only need a few Medibuntu packages, the three I use are realplayer, w64codecs and libdvdcss2. I have them downloaded and saved, so it is easy to install them without setting up the medibuntu repository. I need to make sure they stay current, but that is easy enough.

[http://packages.medibuntu.org/](http://packages.medibuntu.org/)   and choose your version.

---

### Post by bryncoles on 2009-11-01
Cool! Got everything I wanted from that now, though Medibuntu still doesn't seem to have installed. I'll work on that later... for now, on to the next problem!

Cheers guys!

---

### Post by Uncle Spellbinder on 2009-11-01
```
#### Medibuntu - http://www.medibuntu.org/ 
## sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
deb http://packages.medibuntu.org/ karmic free non-free
```

That's how it is in my sources.list. I did *[SIZE="1"]**sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update**[/SIZE]* without issue.

---

