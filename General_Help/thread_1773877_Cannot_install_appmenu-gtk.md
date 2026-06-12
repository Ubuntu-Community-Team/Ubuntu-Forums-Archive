---
title: "Cannot install appmenu-gtk"
date: 2011-06-02
forum: General Help
---

### Post by asuastrophysics on 2011-06-02
Hi everyone,

I'm trying to install ubuntu's appmenu on 10.04 lucid, but I'm running into problems. I followed the instructions from this website:
[https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationMenu](https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationMenu)

It says to first add the repository:
```
jakob@jake-desktop:~$ sudo add-apt-repository ppa:canonical-dx-team/une
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv B830F373C1A4AB09059A12F8AA2BB78B7AE26941
gpg: requesting key 7AE26941 from hkp server keyserver.ubuntu.com
gpg: key 7AE26941: "Launchpad Private PPA for Canonical Desktop Experience Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
jakob@jake-desktop:~$ 

```
I then run apt-get update as root, and I get this suspicious line:
```
Ign http://ppa.launchpad.net/canonical-dx-team/une/ubuntu/ lucid/main Translation-en_US

```
Which is weird, because the source is "checked" in the repos.

If I try to install it, I get this:
```
jakob@jake-desktop:~$ sudo apt-get install appmenu-gtk libqtgui4 indicator-applet-appmenu indicator-appmenu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package appmenu-gtk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package appmenu-gtk has no installation candidate
jakob@jake-desktop:~$ 

```

Anyone know what's going on here, or why the repo is choosing to ignore the required source?

---

### Post by gordintoronto on 2011-06-02
The wiki article begins, "In the 10.10 cycle we are working to bring support to the Ubuntu Netbook Edition..."

Are you using 10.10 Netbook Edition?

---

### Post by asuastrophysics on 2011-06-02
> **gordintoronto said:**
> The wiki article begins, "In the 10.10 cycle we are working to bring support to the Ubuntu Netbook Edition..."

Are you using 10.10 Netbook Edition?

No, I'm using 10.04 LTS. The reason I thought that it was supported under 10.04 was because of the following direct quote from the web page I linked earlier:

"Ubuntu Desktop Installation

For development purposes, a gnome-panel compatible version is also available.

    If you are on **Lucid**, load a terminal and run sudo...."

(the ... goes on to explain how to add the repo and install appmenu)

---

