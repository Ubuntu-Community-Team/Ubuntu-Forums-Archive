---
title: "About repo to download wine-1.1.33"
date: 2009-11-29
forum: General Help
---

### Post by satimis on 2009-11-29
Hi folks,


Ubuntu 8.04


I need to install wine-1.1.33 for testing iTunes 9

The package is on PPA;
[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

I have following repo on /etc/apt/source.list```

deb http://ppa.launchpad.net/jonabeck/ppa/ubuntu hardy main
deb-src http://ppa.launchpad.net/jonabeck/ppa/ubuntu hardy main

```

However running;
$ apt-cache policy wine```

wine:
  Installed: (none)
  Candidate: 1.0.0-1ubuntu4~hardy1
  Version table:
     1.0.0-1ubuntu4~hardy1 0
        500 http://hk.archive.ubuntu.com hardy-updates/universe Packages
     0.9.59-0ubuntu4 0
        500 http://hk.archive.ubuntu.com hardy/universe Packages

```

wine-1.1.33 is not there.

Please advise the repo to be added on source.list and the command for installing respective key.  TIA


B.R.
satimis

---

### Post by kostkon on 2009-11-29
Obviously, you need to add that PPA to your software sources list, that is add these two lines:
```
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu hardy main 
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu hardy main
```

---

### Post by GepettoBR on 2009-11-29
After adding the repos, you have to update your software list by running ```
sudo apt-get update
``` or ```
sudo aptitude update
```
Only then will your computer "see" the software available in the newly-added repo.

> **kostkon said:**
> Obviously, you need to add that PPA to your software sources list, that is add these two lines:
```
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu hardy main 
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu hardy main
```He already did that. Why would you reply without even reading the OP?

---

