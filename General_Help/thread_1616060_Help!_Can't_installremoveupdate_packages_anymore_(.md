---
title: "Help! Can't install/remove/update packages anymore :( :("
date: 2010-11-07
forum: General Help
---

### Post by WG- on 2010-11-07
Well the title says it I can't install or remove or update any package anymore by the "ubuntu software center", "update manager" or "synaptic package manager" :( :( 

When I try to install/remove/update a package the following error is produced:
> installArchives() failed: Setting up install-info (4.13a.dfsg.1-5ubuntu1) ...
/etc/environment: line 4: /proc/asound/card0/pcm0p/oss: No such file or directory
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 install-info
Setting up install-info (4.13a.dfsg.1-5ubuntu1) ...
/etc/environment: line 4: /proc/asound/card0/pcm0p/oss: No such file or directory
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of emacs23:
 emacs23 depends on install-info; however:
  Package install-info is not configured yet.
dpkg: error processing emacs23 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of maxima-emacs:
 maxima-emacs depends on emacs23 | emacsen; however:
  Package emacs23 is not configured yet.
  Package emacsen is not installed.
  Package emacs23 which provides emacsen is not configured yet.
dpkg: error processing maxima-emacs (--configure):
 dependency problems - leaving unconfigured


I think my problem can have 2 causes (first one less probable:

1. Yesterday I was busy configuring Enemy Territory and had problems with the sound. I then download et-sdl-sound from: [http://nullkey.ath.cx/~stuff/et-sdl-sound/](http://nullkey.ath.cx/~stuff/et-sdl-sound/). Maybe that has something to do with it. Because I saw:
> /etc/environment: line 4: /proc/asound/card0/pcm0p/oss: No such file or directory Pretty often yesterday when I tried several methods ([https://help.ubuntu.com/community/EnemyTerritory#Sound Issues]("https://help.ubuntu.com/community/EnemyTerritory#Sound Issues")) to fix the sound in ET. 

2. The problem started after I installed scilab from the ubuntu software center and wanted to remove afterwards because I noticed that it wasn't the latest version and wanted to install it then from the website of scilab. I also see a "emacs" a lot in occure above which was installed with scilab so I guess it has to do something with it as well.

My question is: how do I fix this :'( :'( I really don't know how. I'm still too newbie with ubuntu for that. 

ps. When installing scilab I also optionally installed this:
- Scientific software package (english documentations)
- Scilab Wavelet and signal processing toolbox
- Scilab module for artificial neural networks
- "Matlab-like" Plotting library for Scilab

---

### Post by WG- on 2010-11-07
Before anyone asks /etc/environment contains:
> PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANGUAGE="en"
LANG="en_US.utf8"
echo et.x86 0 0 direct > /proc/asound/card0/pcm0p/oss
echo et.x86 0 0 disiable > /proc/asound/card0/pcm0c/oss

---

### Post by corrytonapple on 2010-11-07
> **WG- said:**
> 
ps. When installing scilab I also optionally installed this:
- Scientific software package (english documentations)
- Scilab Wavelet and signal processing toolbox
- Scilab module for artificial neural networks
- "Matlab-like" Plotting library for Scilab
Although I don't know the name of the files you installed from the software center, I can give you the general code you can type in for removing applications from the Terminal. Go to **Applications>Accessories>Terminal**. Then type:
```

sudo apt-get purge [COLOR=Lime]application[/COLOR]

```
Assuming the name is "Scilab", I think, but am not sure, you would type:
```

sudo apt-get purge scilab

```
Try those. Also, are you an Administrator? Does the Ubuntu Software Center even open?

---

### Post by Cheesehead on 2010-11-07
Take lines #4 and #5 ('disable' is misspelled, by the way) out of /etc/environment, then try package management again.

It's doubtful those lines are helping anyway, since your seem to be directing to a process that doesn't exist.

---

### Post by WG- on 2010-11-07
Yes I'm an administrator.

---

### Post by corrytonapple on 2010-11-07
> **WG- said:**
> Yes I'm an administrator.
OK, then I doubt it is a permissions problem. Try what Cheesehead said, then try what I have put.

---

### Post by WG- on 2010-11-08
Just removing the file helped solve the problem :)

---

### Post by corrytonapple on 2010-11-08
> **WG- said:**
> Just removing the file helped solve the problem :)
Just removing the files you installed? How did you uninstall them? Glad to hear it works again. :)

---

### Post by WG- on 2010-11-08
No, the /etc/environment file ;)

---

### Post by corrytonapple on 2010-11-08
> **WG- said:**
> No, the /etc/environment file ;)
Glad to hear it works. I will note that as a fix for future reference. :)

---

### Post by WG- on 2010-11-08
> **corrytonapple said:**
> Glad to hear it works. I will note that as a fix for future reference. :)

Really wierd still however. Since I don't know why /etc/environment should be "called" when a package is installed/upgraded/removed. Also why that simple lines did so much "damage" that it couldn't install/upgrade/remove a package.

---

