---
title: "Synaptic error message"
date: 2006-06-14
forum: General Help
---

### Post by Dr. Feelgood on 2006-06-14
I open up Synaptic now, and I get this error message:

W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://theli.free.fr](http://theli.free.fr) ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)

It still works as it should but it gives me that annoying message everytime.  What can I do to fix it?  And more importantly....what went wrong?

---

### Post by 23meg on 2006-06-14
Maybe those repositories were down at some point; did you do a ```
sudo apt-get update
```?

---

### Post by Dr. Feelgood on 2006-06-14
This is the error I got from that:

Fetched 4B in 10s (0B/s)
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz)  404 Not Found
Failed to fetch [http://theli.free.fr/packages/breezy/./Packages.gz](http://theli.free.fr/packages/breezy/./Packages.gz)  404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz)  404 Not Found
Reading package lists... Done
W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://theli.free.fr](http://theli.free.fr) ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Dr. Feelgood on 2006-06-18
anyone have any ideas for me?

---

### Post by ifokkema on 2006-06-20
[QUOTE=Dr. Feelgood]
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz)  404 Not Found[/QUOTE]
This site has no ubuntu directory left (just tested that). Whatever you were downloading from that site - pick another mirror. Until then, just remove or quote the line from your /etc/apt/sources.list file.

[QUOTE=Dr. Feelgood]Failed to fetch [http://theli.free.fr/packages/breezy/./Packages.gz](http://theli.free.fr/packages/breezy/./Packages.gz)  404 Not Found[/QUOTE]
This site has switched to dapper ([http://theli.free.fr/packages/dapper/](http://theli.free.fr/packages/dapper/) exists). See above: find other mirror or remove from your sources.list.

---

### Post by Dr. Feelgood on 2006-06-20
Thanks for the info, problem solved.

---

