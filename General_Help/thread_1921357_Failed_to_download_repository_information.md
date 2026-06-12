---
title: "Failed to download repository information"
date: 2012-02-06
forum: General Help
---

### Post by mersiuse on 2012-02-06
when i try to update this error appears 

W:Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

what shall i do ?

---

### Post by cortman on 2012-02-06
The two online repositories specified in the error have gone 404, no longer accessible. You can remove them from your sources.list file by opening a terminal (ctrl+alt+t) and copy/pasting the following code in-

```
gksu gedit /etc/apt/sources.list
```

This will open sources.list in a your text editor. Find and delete the lines that have

```
http://ppa.launchpad.net/stebbins/ha...-i386/Packages 
http://ppa.launchpad.net/stebbins/ha...source/Sources
```

in them (just delete the whole line), and save it. This'll prevent error messages in the future.

---

