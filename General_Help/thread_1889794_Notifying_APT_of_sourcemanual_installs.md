---
title: "Notifying APT of source/manual installs?"
date: 2011-12-02
forum: General Help
---

### Post by GrantStoner on 2011-12-02
How does one go about notifying APT of something installed by source? For example, I installed Aircrack-ng from SVN (because of issues I had with the .deb from the repos) but upon installing Fern Wifi Cracker from its .deb, dpkg doesn't recognize that Aircrack-ng is already installed so it fails. I build a lot from sauce, but it's never really created dependency problems for me in the past - so how do I go about notifying APT of source/manual installs?

---

### Post by GrantStoner on 2011-12-02
To be clear, I know I can tell dpkg not to check for dependencies, force install, etc. But I would like to also know how to tell dpkg/APT when I've made changes its not aware of.

---

### Post by Lars Noodén on 2011-12-02
The way I've done it in the past was to roll my own package and then use dpkg to install it.

---

### Post by GrantStoner on 2011-12-02
Hrm. I suppose I could do that - it would solve this specific instance. But I'd like a command I can use for every program I install, so that all of them are recognized as "installed" in APT/dpkg. There's around a few hundred I've manually tweaked, configured, and installed that I'd rather not have to repackage and reinstall.

---

