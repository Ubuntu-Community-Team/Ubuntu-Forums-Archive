---
title: "Failed To Download Repository Information"
date: 2010-12-16
forum: General Help
---

### Post by mikmalot on 2010-12-16
I keep getting a notification that my update information is outdated, so I go into the update manager. It says I am up to date, but to try to make the notification go away, I tell it to check for updates, and I get this error message:

Failed to download repository information

Check your Internet connection.

Details:
W:Failed to fetch [http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

Thoughts?

-edit: I think I figured it out myself. For anyone who may have the same (or similar problems) here's what I did:

clicked settings at the bottom of the update manager, then clicked the "other software" tab, and unchecked the offending packages.

---

### Post by karmila on 2010-12-16
Hi mikmalot, 

Just like the message says that link was not found.

You need to delete/disable that ppa from software sources and then do the update again.

---

### Post by garvinrick4 on 2010-12-16
Open a terminal:
```
gksudo gedit /etc/apt/sourcs.list
```
Now put a comment sign in front of offending ppa's (#). and hit save.
```
sudo apt-get update
```
done.

---

### Post by HebrewTheHammer on 2010-12-18
hey guys, im using 8.10 and i am having the same problem, is there anything you guys could tell me?

---

