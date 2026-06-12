---
title: "Firefox in Repos is very old"
date: 2011-07-06
forum: General Help
---

### Post by strange_cathect on 2011-07-06
I'm running Ubuntu 10.10 and the repos only have Firefox 3.6.18. Is there any reason why there is not a newer version in the Repos?

There is a linux version 5.0 for Firefox. Any reason I should upgrade to it?

Confused...

---

### Post by uRock on 2011-07-06
> **strange_cathect said:**
> I'm running Ubuntu 10.10 and the repos only have Firefox 3.6.18. Is there any reason why there is not a newer version in the Repos?

There is a linux version 5.0 for Firefox. Any reason I should upgrade to it?

Confused...
3.6 is still receiving security updates. If you wish to upgrade to Firefox5, which is much faster than FF4 and 3.6, then you can do it by simply running the following commands to install the PPA for the Firefox stable repo, then running updates;```
sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by ajgreeny on 2011-07-06
> **uRock said:**
> 3.6 is still receiving security updates. If you wish to upgrade to Firefox5, which is much faster than FF4 and 3.6, then you can do it by simply running the following commands to install the PPA for the Firefox stable repo, then running updates;```
sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update && sudo apt-get upgrade
```
For those still using 10.04, this ppa also works well for you.  FF5 is very good in my opinion.

---

### Post by strange_cathect on 2011-07-06
Thanks for the replies. But I was just wondering why 10.10 isn't pushing an upgrade automatically through the official repos.

---

### Post by uRock on 2011-07-06
> **strange_cathect said:**
> Thanks for the replies. But I was just wondering why 10.10 isn't pushing an upgrade automatically through the official repos.
Canonical will only change the version in the repo if Mozilla drops support for 3.6.

---

