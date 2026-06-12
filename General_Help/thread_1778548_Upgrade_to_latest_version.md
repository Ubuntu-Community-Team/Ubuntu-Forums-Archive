---
title: "Upgrade to latest version"
date: 2011-06-09
forum: General Help
---

### Post by johnb39 on 2011-06-09
I am running 10.10 and I am invited to upgrade to 11.04. When I click yes, the inttallation process asks me to insert an old Ubuntu disto 6.06. I have the disk, but when I put it into the cd drive, nothing happens. Why is it asking for a ubuntu version I have never had installed? I wish that there was an accessible "help" column

---

### Post by JRV on 2011-06-09
Open synaptic and click on Settings=>Repositories.
Look for "Cdrom with Ubuntu 6.06" under the Ubuntu Software
and the Other Software tabs.  

If you find it uncheck it.
Then open a terminal and enter the command:

```
sudo apt-get update
```

---

### Post by seawolf167 on 2011-06-09
Follow JRV's post for a resolution, see here for the [how-to]("https://help.ubuntu.com/community/NattyUpgrades") if you are unsure about any steps.

---

### Post by johnb39 on 2011-06-09
> **JRV said:**
> Open synaptic and click on Settings=>Repositories.
Look for "Cdrom with Ubuntu 6.06" under the Ubuntu Software
and the Other Software tabs.  

If you find it uncheck it.
Then open a terminal and enter the command:

```
sudo apt-get update
```
Thank you

---

