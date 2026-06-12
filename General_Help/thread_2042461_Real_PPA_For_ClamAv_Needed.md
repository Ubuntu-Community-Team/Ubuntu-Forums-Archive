---
title: "Real PPA For ClamAv Needed"
date: 2012-08-14
forum: General Help
---

### Post by tecknomage on 2012-08-14
**REF:** Ubuntu 12.04

I've tried various methods and sites to **install the correct, working PPA for ClamAv**.

I get referred to....

[LIST]
[*][https://launchpad.net/~ubuntu-clamav/+archive/ppa]("https://launchpad.net/%7Eubuntu-clamav/+archive/ppa")
[*][https://wiki.ubuntu.com/MOTU/Clamav](https://wiki.ubuntu.com/MOTU/Clamav)
[/LIST]
...by numerous pages, BUT (*for me*) they are totally confusing. **Neither provides the EXACT Terminal Command to install the correct, current, ClamAv PPA for Ubuntu 12.40**.

](*,)**PLEASE, what is the current Terminal Command for Ubuntu's ClamAv PPA?** One that worked within the last few weeks.

**NOTE:** I had a *launchpad.ne*t PPA way back but Updater cannot reach it.

---

### Post by ubudog on 2012-08-14
To add the Launchpad PPA for ClamAV (the first link in your post), type the following commands into a terminal.

```
sudo add-apt-repository ppa:ubuntu-clamav/ppa
```
(adds the PPA)

```
sudo apt-get update
```
(updates the repository information)

```
sudo apt-get install clamav
```
(should install the latest ClamAV version)

Hope that helps,
ubudog

---

### Post by tecknomage on 2012-08-15
> **ubudog said:**
> To add the Launchpad PPA for ClamAV (the first link in your post), type the following commands into a terminal.

```
sudo add-apt-repository ppa:ubuntu-clamav/ppa
```(adds the PPA)

```
sudo apt-get update
```(updates the repository information)

```
sudo apt-get install clamav
```(should install the latest ClamAV version)

Hope that helps,
ubudog

THANKS :D

Now, will this allow automatic _virus definition_ and *ClamTK* update?

---

### Post by raja.genupula on 2012-08-15
Thats you have to configure your self from its preference .

---

### Post by kitterma on 2012-08-19
No.  You don't need a "Real PPA for ClamAV".  The current clamav release is available from the Ubuntu archive for all releases.  If you're running 11.04 or later it's a simple matter of applying all the available regular system updates.  If you're on 8.04 or 10.04 you have to enable the backports repository.  It's there to be installed.  No PPA needed.

---

