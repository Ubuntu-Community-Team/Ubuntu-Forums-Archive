---
title: "upgrade 10.10 to 11.04"
date: 2011-04-28
forum: General Help
---

### Post by sainath90 on 2011-04-28
presently im using ubuntu 10.10.how can i upgrade to 11.04

---

### Post by 3Miro on 2011-04-28
If you go to System -> Admin -> Software Updates, there should be an option at the top. If not, you can type in terminal:

```
sudo apt-get update
sudo apt-get upgrade -d
```

Upgrades may or may not work, backup everything important first so that you don't lose anything if you have to go for a reinstall.

Note that 11.04 is a big change so I hope you are prepared for it.

---

### Post by clhsharky on 2011-04-28
sainath90


Upgrade Notes 
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

> Using packages from repositories not controlled by Ubuntu is not recommended as it can be a security risk and may break or complicate your upgrade. If you have used EasyUbuntu or Automatix (neither of which is recommended nor supported), you may have problems upgrading to a newer version and may require a fresh install. If you have installed software from other sources, the upgrade may go more smoothly if you remove this software before attempting the upgrade.
From 10.10 to 11.04
[https://help.ubuntu.com/community/NattyUpgrades](https://help.ubuntu.com/community/NattyUpgrades)


Sharky

---

### Post by Frogs Hair on 2011-04-28
The upgrade option should appear in the update manager soon and already has for some .

---

### Post by Hedgehog1 on 2011-04-28
Another 'safer' option is to upgrade using the LiveCD/LiveUSB:

[IMG]http://img848.imageshack.us/img848/874/upgradetonatty.png[/IMG]


This will run **much faster**, as well.

Please backup your documents, whatever method you choose!


***The Hedge***

:KS

---

