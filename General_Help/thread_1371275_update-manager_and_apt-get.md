---
title: "update-manager and apt-get"
date: 2010-01-03
forum: General Help
---

### Post by vientito on 2010-01-03
I have an observation on my ubuntu karmic.  I am perplexed at the said behaviour.  I hope someone will give me some explanation.  for more than twice, I have noticed that if I register a new development repository and proceed to update and install the new stuffs by using apt-get, after that update and installation my update-manager simply does not know that so it will give me a list of "new" installations to be installed.  how come that update-manager, being an front end based on APT, would not get the message new stuffs have already been added and installed.  I am tired of this repeated installation.

---

### Post by starcraft.man on 2010-01-03
I think I know the situation your talking about. You don't have to install said updates from update-manager if you know you've installed them via apt. The update-manager updates on it's own schedule (set in the options for sources I believe), it is possible that it pulls a list of packages at time a and is ignored/not updated while you install them via apt from terminal. If this occurs, just ask it to check for updates, it has to see what's been updated and delist already installed when doing a check against repos/current install.

As an alternate solution, you can always disable automatic updates. Click settings in the Update-manager window, just be sure to stay up to date manually.

---

