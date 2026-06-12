---
title: "How to get rid of Xbmc repository"
date: 2011-06-03
forum: General Help
---

### Post by royalflush5 on 2011-06-03
Hello everyone, when I use the update manager, or use the terminal to search for updates, I get this error message:

W:Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Now, i know this is a problem with Xbmc (which worked like trash) but I have no clue now to remove it, Ive tried to reinstall it, using the purge and auto remove commands, but no such luck.
anyone have an idea?

---

### Post by linuxinstalledfromhdd on 2011-06-03
Open synaptic package manager.
```

sudo synaptic

```
And then you want to navigate to 

Settings

and then

Repositories

and then

Other Software

and remove whatever listings that are bugging you. :)

---

