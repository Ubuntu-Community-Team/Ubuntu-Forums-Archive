---
title: "Handbrake Installation Problems"
date: 2011-11-22
forum: General Help
---

### Post by meloade on 2011-11-22
When adding the neccesary repos to my sources, there's an error in updating them


W: Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

I was just wondering if the servers are down temporarily or I misspelt something somewhere.
Also when attempting to install the deb file that would normally be downloaded from that source, it's unable to satisfy the dependency of 'libnotify1'.

Thanks for reading and if you comment, bless your face.:KS

---

### Post by papibe on 2011-11-22
Which ppa did you use?

This is how I installed it:
```
$ sudo add-apt-repository ppa:stebbins/handbrake-snapshots
$ sudo apt-get update
$ sudo apt-get install handbrake-gtk
```
Regards.

---

### Post by meloade on 2011-11-23
> **papibe said:**
> Which ppa did you use?

This is how I installed it:
```
$ sudo add-apt-repository ppa:stebbins/handbrake-snapshots
$ sudo apt-get update
$ sudo apt-get install handbrake-gtk
```
Regards.

Thanks, it worked. I'm not sure if it was me restarting my computer or that the server was down but it worked nonetheless. Yes, this is the same PPA I used originally but your comment urged me to give it another try and for that I thank you, good sir.

---

