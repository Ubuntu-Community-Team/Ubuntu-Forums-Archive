---
title: "find deluge 1.1.9"
date: 2009-11-06
forum: General Help
---

### Post by aykydo on 2009-11-06
Hello!!!

My torrent tracker does not support deluge 1.2 RC.
How can find **Deluge 1.1.9**(or previous from 1.2 RC )? 
I can't find it in the repositories or on the deluge website for download ([http://deluge-torrent.org/](http://deluge-torrent.org/)).
I am looking for the deb file or a repository.
Using Ubuntu 9.10 64

Thank You!

---

### Post by alphaniner on 2009-11-06
According to packages.ubuntu.com, the version of deluge in the Karmic repository is 1.1.9.

And from my Karmic VM:
```

$ aptitude show deluge
Package: deluge
State: not installed
Version: **1.1.9**+dfsg-1
```

---

### Post by aykydo on 2009-11-06
When I install Deluge it installs me deluge 1.2.0 RC

```

$ aptitude show deluge
Package: deluge
State: installed
Automatically installed: no
Version: 1.2.0~rc3-2~karmic~ppa1
```

---

### Post by alphaniner on 2009-11-06
```
Version: 1.2.0~rc3-2~karmic~**[COLOR="Red"]ppa[/COLOR]**1
```

It looks to me like you have the deluge PPA enabled, and the version from there 'overrides' the version in the standard repositories.  I advise you **sudo apt-get purge deluge** or **sudo apt-get remove deluge** (purge will remove config files)*, then remove or comment out the deluge PPA in your sources file (/etc/apt/sources.list), then reload packages (**sudo apt-get update**), then run **aptitude show deluge** again.

*You should also remove any other deluge packages such as deluge-common, deluge-core, etc. if any such packages are installed.  Do **aptitude search deluge** to find if any such packages are installed, they will show up with an i such as```
[COLOR="Red"]i[/COLOR]   deluge                          - bittorrent client written in Python/PyGTK 
[COLOR="Red"]i[/COLOR]   deluge-common                   - bittorrent client written in Python/PyGTK 
[COLOR="Red"]i[/COLOR]   deluge-console                  - bittorrent client written in Python/PyGTK 

```

---

### Post by scouser73 on 2009-11-06
If you have Deluge 1.1.2RC installed then remove it via Synaptic Package Manager, and then install Deluge 1.1.9: [[COLOR="Red"]**Deluge 1.1.9 from the GetDeb website**[/COLOR]]("http://www.getdeb.net/release/4466")

You'll need to remove the Deluge PPA that you have installed, that can be done by going to Software Sources, click the Third Party Sources tab, and removing Deluge.

---

### Post by aykydo on 2009-11-06
Thank you!
Now I have installed Deluge 1.1.9!

---

