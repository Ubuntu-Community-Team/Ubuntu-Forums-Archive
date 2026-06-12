---
title: "Trying to Downgrade VLC"
date: 2012-02-28
forum: General Help
---

### Post by sideffects on 2012-02-28
I have uninstalled vlc, and removed the ppa. I have also used ppa-purge. However, when I attempt to reinstall vlc via the terminal, this is the error i receive back.


```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vlc : Depends: vlc-nox (= 1.1.12-2~oneiric1) but it is not going to be installed
       Depends: libvlccore4 (>= 1.1.0) but it is not going to be installed
       Recommends: vlc-plugin-notify (= 1.1.12-2~oneiric1) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 1.1.12-2~oneiric1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

Any solutions?

EDIT: Well, as I continued tinkering, I found the solution. I simply needed to manually remove vlc-data. I have no idea why that didn't remove itself with the uninstall and/or purge.

---

