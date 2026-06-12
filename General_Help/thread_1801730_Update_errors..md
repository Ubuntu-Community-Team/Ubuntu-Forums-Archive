---
title: "Update errors."
date: 2011-07-11
forum: General Help
---

### Post by joelstitch on 2011-07-11
I am getting this errors when I check for new updates:

```
W:Failed to fetch http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

How would I go about fixing this issue?

---

### Post by macaholic on 2011-07-11
That means it can't find the packages for natty at the ppa, i.e., the ppa maintainers haven't updated it for natty yet.

If you want to install the packages for maverick from the ppa and avoid the errors, you can do the following: go into the Ubuntu Software Center,  Edit>Software Sources, find the ppa reposiories for xmbc, and edit them to change the distribution from natty to maverick.

---

