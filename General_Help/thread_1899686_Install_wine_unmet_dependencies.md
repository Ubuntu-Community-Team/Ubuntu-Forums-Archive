---
title: "Install wine unmet dependencies"
date: 2011-12-24
forum: General Help
---

### Post by newbie234 on 2011-12-24
I tried to install Wine onto my Ubuntu 10.04 which is running on a Apple PPC

I typed in:
```
gksudo apt-get install wine
```And got:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: wine1.2 but it is not installable
```I don't know what to do, I really want to use Wine. Anyone help? :(

---

### Post by cottfcfan on 2011-12-24
Try a latter version of wine.
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```
```
sudo apt-get update && sudo apt-get install wine1.3
```

---

