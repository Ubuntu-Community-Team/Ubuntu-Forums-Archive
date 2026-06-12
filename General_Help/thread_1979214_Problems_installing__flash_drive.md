---
title: "Problems installing  flash drive"
date: 2012-05-13
forum: General Help
---

### Post by Camilia on 2012-05-13
I download adobe flash drive for linux tar.gz. It is opened by archive manager. I never get the option to install it. I just see the file.

What can I do so to view videos?

---

### Post by wilee-nilee on 2012-05-13
You would not use a tar from adobe, install the ubuntu-restricted-extras if kubuntu it would be kubuntu-restricted-extras. If Xubuntu or lubuntu sub them in instead.

Make sure you use the ubuntu software center first before the web, most of what you need is in the repos.

---

### Post by Camilia on 2012-05-14
> **wilee-nilee said:**
> You would not use a tar from adobe, install the ubuntu-restricted-extras 
Tried to and got message remove libav codeclibrary
and libav utility library. Tried suddo remove. Nothing happened.

---

### Post by jocko on 2012-05-14
> **Camilia said:**
> Tried to and got message remove libav codeclibrary
and libav utility library. Tried suddo remove. Nothing happened.
The package manager should be able to handle the dependencies.
Try these commands in a terminal:
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```
When the package manager asks you if it is ok to remove those two packages, just press "y" to accept it. They will be replaced by other packages that include more codecs, so you won't miss anything.

---

### Post by Camilia on 2012-05-14
> **jocko said:**
> 
Try these commands in a terminal:
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

Had no problem with sudo apt-get update 
with sudo apt-get install ubuntu-restricted-extras terminal stuck on Configuring ttf-mscorefonts-installer for 4hrs. I closed it.

Reinstalled. Missing plugins appeared. Downloaded 1, can't remember which 1. Option to download second 1, flash drive did not appear when tried to find missing plugins. Now can view videos on you tube but not on comcast website.

Installed upgrades and flash drive got downloaded. Now unable to download videos on you tube or comcast.

---

