---
title: "Update gives error message about Deluge"
date: 2010-01-28
forum: General Help
---

### Post by danootz on 2010-01-28
Hi. Whenever Ubuntu tries to update itself or if I initiate an update I can install every but Deluge's update.

I get the following:

AN ERROR HAS OCCURE:
E: /var/cache/apt/archives/deluge-common_1.2.0-2~karmic~ppa1_all.deb: trying to overwrite '/usr/share/pyshared/deluge-1.2.0.egg-info/dependency_links.txt', which is also in package deluge-core 0

What does this mean? It suggests filtering broken to fix it. I do so and mark deluge for reinstallation but it doesn't seem to solve anything.

Thanks guys.

---

### Post by x33a on 2010-01-28
Try manually re-installing the package.
```
sudo apt-get remove <pkg>
```
then ```
sudo apt-get update && apt-get install <pkg>
```

---

### Post by danootz on 2010-01-28
It's really weird...

First of all I can run Deluge.
I get the update error. I try the broken fix thing and no go.
I tried the command line "sudo apt-get remove deluge" and I get this error:

[I]Package deluge is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  deluge-gtk: Depends: deluge-common (= 1.2.0-2~karmic~ppa1) but 1.2.0-1~getdeb2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[/I]

It's not allowing me to remove anything.

---

### Post by x33a on 2010-01-28
try
```
[I]sudo apt-get -f install
```

or try
```
sudo apt-get remove deluge-common deluge-gtk
```
[/I]

---

### Post by danootz on 2010-01-29
Thanks for all your help x33a.

I had tried what you recommended and it was still giving me errors. I forget how I did it but I eventually managed to uninstall Deluge and turned of the sources for the Deluge PPA and just reinstalled via a GETDEB package.

Thanks again! :D

---

### Post by x33a on 2010-01-30
Great that the problem got solved. Also, you can give transmission a try. it has improved a lot lately. and if you are a console addict, then rtorrent is the way to go (i use it and love it).

---

### Post by danootz on 2010-02-02
Thanks again. Yeah I tried Transmission a while back. I could give it a run again. I just remember there being an issue with speeds even when i tried to configure ports and all that.

---

