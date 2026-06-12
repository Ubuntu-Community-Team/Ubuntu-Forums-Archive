---
title: "Update Manager/Apt-Get Update problems; seem pretty major"
date: 2011-10-15
forum: General Help
---

### Post by mowdownjoe on 2011-10-15
So, I recently updated to 11.10 on my Wubi install, and anytime I try to use update manager or run apt-get update from the terminal, these errors pop up:
```
W:Failed to fetch http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```Now, I know what an [Error 404]("http://xkcd.com/404/") is. My question is why? Why is it that when I updated Ubuntu, it went and added a bunch of non-existent PPAs? And does anyone know the correct URLs so I can change them and fix this mess?

[Edit:] Comparing the list of PPAs on my Wubi install to the one on my Cr-48 is making me wonder if those ones that are 404-ing on me are even essential. Any takers on this bit? Admittedly, updating my Wubi install was a bit problematic... it tried to clean off some unneeded packages, and then my RAT5 wouldn't let me click through them to check them out one-by-one... I just restarted right there and used Computer Janitor to remove the packages the update wanted to remove. So... I'm guessing it also forgot to remove a PPA or 3? I dunno... I'm guessing.

---

### Post by effenberg0x0 on 2011-10-15
Try this:

```

if [ ! -d "/run" ]; then sudo mkdir /run && sudo mkdir /run/lock && sudo rm -rf /var/run && sudo rm -rf /var/lock && sudo ln -s /run /var/run && sudo ln -s /run/lock /var/lock; fi
sudo rm -rf /var/lib/apt/lists/partial/* 
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup 
sudo mkdir ~/sources.list.d && sudo mv /etc/apt/sources.list.d/* ~/sources.list.d/ 
sudo sed -i s'/us.//g' /etc/apt/sources.list 
sudo apt-get update

```

Your question: There seems to be some punctual situations in which the old /var and /var/lock structure is not properly moved to /run and /run/lock (new standard). We also have two us* entries in sources.list that are not working for the last 24 hours or more. Cache lists get corrupted.

Please report back.


Regards,
Effenberg

---

