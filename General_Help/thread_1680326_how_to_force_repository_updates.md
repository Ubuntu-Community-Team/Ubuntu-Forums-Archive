---
title: "how to force repository updates"
date: 2011-02-02
forum: General Help
---

### Post by hwttdz on 2011-02-02
So I just added a ppa, which has version 1.1.6 of vlc, however I do not have the ability to upgrade vlc, and when I run update it ignores "Ign" the ppa, because it thinks it fetched the most recent data.  How can I clear out the stale data to force an update?

---

### Post by kostkon on 2011-02-02
> **hwttdz said:**
> So I just added a ppa, which has version 1.1.6 of vlc, however I do not have the ability to upgrade vlc, and when I run update it ignores "Ign" the ppa, because it thinks it fetched the most recent data.  How can I clear out the stale data to force an update?
Did you run
```
sudo apt-get upgrade
```
first (or equivalently, pressed *Check* in the Update Manager)?

You could check what versions of vlc are available in your repos, by giving
```
apt-cache policy vlc
```
and pasting the output here, if you want.

---

