---
title: "Repositories for 11.04 -- error"
date: 2011-05-31
forum: General Help
---

### Post by saggio on 2011-05-31
So, I upgraded to 11.04 upon release from the last LTS, and although I ran into some issues it's been pretty smooth sailing. There is one nagging thing that I'm concerned about, though: an error I get when updating apt/synaptic.

Whenever I attempt to check for new software updates, this is the error that I receive --

```
W:Failed to fetch http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

I'm quite sure that it's not a network error on my end, as I'm quite able to access the internet and do absolutely everything I would normally do. I've also not modified my /etc/apt/sources.list file manually in years, so I'm kind of stumped how this is happening.

Presumably the fix is to modify the relevant lines in my /etc/apt/sources.list, but if the above URLs *aren't* correct, what is? 

Thanks!

---

### Post by linuxinstalledfromhdd on 2011-05-31
you need to go into synaptic and disable those repositories, and hit reload until the problem stops..   Then you need to search for the PPAs via a search engine, and find the PPA instructions to reinstall them from the terminal.

---

### Post by plucky on 2011-05-31
> W:Failed to fetch [http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found


There is no PPA for the Natty Distribution,only for Lucid & Maverick.

See [Here](http://ppa.launchpad.net/elegant-gnome/ppa/ubuntu/dists/)

Good Luck

---

### Post by garvinrick4 on 2011-05-31
```
gksudo gedit /etc/apt/sources.list
```Now put a # sign in front of offending line or change to maverick or lucid and hit save button upper left.
```
sudo apt-get update
```

---

