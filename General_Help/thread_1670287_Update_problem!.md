---
title: "Update problem!"
date: 2011-01-18
forum: General Help
---

### Post by chrissy.millichamp on 2011-01-18
Ive had recently encountered two error messages every time that I want to update my ubuntu system, which is the following, W: Failed to fetch [http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found , and the second one is,  E: Some index files failed to download, they have been ignored, or old ones used instead.

Help anyone?

---

### Post by plucky on 2011-01-19
> **chrissy.millichamp said:**
> Ive had recently encountered two error messages every time that I want to update my ubuntu system, which is the following, W: Failed to fetch [http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found , and the second one is,  E: Some index files failed to download, they have been ignored, or old ones used instead.

Help anyone?

Remove that PPA from your sources.list as it doesn't have a repository for Maverick.

See [Here](http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/)

Good Luck

---

### Post by chrissy.millichamp on 2011-01-19
I cant find the following: 
[http://ppa.launchpad.net/gdm2setup/g...rce/Sources.gz]("http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/source/Sources.gz") from my software source list.

---

### Post by siwelchungster on 2011-01-19
are you looking at the actual sources.list or the one in the Ubuntu Software Center?

try:

```
sudo gedit /etc/apt/sources.list
```

and remove the ppa from there

---

### Post by chrissy.millichamp on 2011-01-20
Theres only of these few lines containing, deb [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) maverick main ## Cairo-Dock-PPA-Stable
deb [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) maverick main ## Cairo-Dock-PPA-Stable

---

### Post by plucky on 2011-01-20
> I cant find the following:
[http://ppa.launchpad.net/gdm2setup/g...rce/Sources.gz](http://ppa.launchpad.net/gdm2setup/g...rce/Sources.gz) from my software source list. 


Are you using the GUI? It will be under the **Other Software** tab.

> **siwelchungster said:**
> are you looking at the actual sources.list or the one in the Ubuntu Software Center?

try:

```
sudo gedit /etc/apt/sources.list
```

and remove the ppa from there

It might also be in /etc/apt/sources.list.d

To see if it is there ```
ls -l /etc/apt/sources.list.d
```


Good Luck

---

