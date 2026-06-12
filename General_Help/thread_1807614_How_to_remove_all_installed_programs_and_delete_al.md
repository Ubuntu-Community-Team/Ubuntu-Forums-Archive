---
title: "How to remove all installed programs and delete all files"
date: 2011-07-19
forum: General Help
---

### Post by stamatiou on 2011-07-19
Hey guys, I would like to know if I can delete all of my files and remove all programs from my ubuntu laptop, like a clean install but without having to install the drivers and going through the installation

---

### Post by haqking on 2011-07-19
> **stamatiou said:**
> Hey guys, I would like to know if I can delete all of my files and remove all programs from my ubuntu laptop, like a clean install but without having to install the drivers and going through the installation


mmm weird request.

you could delete your account and choose to remove all files when you do so as long as you have a backup account to administer the system.

---

### Post by 2F4U on 2011-07-19
Removing the programs that you have installed is going to be difficult, since these are not connected to your user. To get rid of your files is easier, since usually, all your files are located in your home folder. However, if you mean to also remove configuration changes you made, that will be much more difficult and it would certainly be easier to do a fresh installation.

---

### Post by haqking on 2011-07-19
> **2F4U said:**
> Removing the programs that you have installed is going to be difficult, since these are not connected to your user. To get rid of your files is easier, since usually, all your files are located in your home folder. However, if you mean to also remove configuration changes you made, that will be much more difficult and it would certainly be easier to do a fresh installation.

+1

easier to not install things unless you want them and keep a record of what you do removal later.

or just do a fresh install, wont take long.

or restore to a backup you made upon fresh install (presuming you did so of course ;-)

---

### Post by Dangertux on 2011-07-19
This is why I am all for doing a software inventory on your home systems. 

Many people act like it's something that only IT departments do but you would be surprised how many individuals have no clue what software they've installed. 

In my opinion start fresh, make a backup of everything as it is immediately after the install then also as you install things keep a log of what your system has on it.

---

### Post by oldos2er on 2011-07-19
APT keeps track of every installed package already; in Synaptic, File, History; **dpkg --get-selections**, etc.

---

### Post by nothingspecial on 2011-07-19
If you have installed everything with apt-get then this should do it. Obviously, I've not tested this.

```
for f in "$(grep 'apt-get install' /var/log/apt/history.log)"; do sudo apt-get remove ${f//Commandline: apt-get install /}; done && sudo apt-get autoremove
```

---

