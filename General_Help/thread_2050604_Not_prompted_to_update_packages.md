---
title: "Not prompted to update packages"
date: 2012-08-31
forum: General Help
---

### Post by jba6511 on 2012-08-31
Running Ubuntu 12.04 and I no longer am notified when updates are available. If I run apt-get update && apt-get upgrade I will see there are new packages and apply the updates, I am just not getting notified like I did before the upgrade.


b@ubuntuDesktop:~$ ps auxf | grep -i  upgrade
b    15683  0.0  0.0   4368   848 pts/1    S+   07:28   0:00          |   |       \_ grep --color=auto -i upgrade
b@ubuntuDesktop:~$

---

### Post by plucky on 2012-08-31
> **jba6511 said:**
> Running Ubuntu 12.04 and I no longer am notified when updates are available. If I run apt-get update && apt-get upgrade I will see there are new packages and apply the updates, I am just not getting notified like I did before the upgrade.


b@ubuntuDesktop:~$ ps auxf | grep -i  upgrade
b    15683  0.0  0.0   4368   848 pts/1    S+   07:28   0:00          |   |       \_ grep --color=auto -i upgrade
b@ubuntuDesktop:~$

12.04 will only notify you once a week if there are no security updates to install.

It will notify you immediately if there **are** security updates.

I believe it checks for updates once a day.(but don't quote me on this)

Good Luck

---

### Post by Frogs Hair on 2012-08-31
Open the update manager > settings to view/set how often updates are checked for.

---

