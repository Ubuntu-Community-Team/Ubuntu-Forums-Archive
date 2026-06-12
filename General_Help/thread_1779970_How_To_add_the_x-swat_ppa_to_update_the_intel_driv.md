---
title: "How To add the x-swat ppa to update the intel driver?"
date: 2011-06-11
forum: General Help
---

### Post by pawan98 on 2011-06-11
Hi, theres been some problems with my desktop and I need to fix it, a person said 
add the x-swat ppa to update the intel driver  but I have no idea how to do that. My graphics card is intel 82865G graphics controller. Thanks.[]("http://askubuntu.com/users/4203/uri-herrera")

---

### Post by pqwoerituytrueiwoq on 2011-06-11
```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
```

---

### Post by pawan98 on 2011-06-11
I done that ^:

pawan@pawan:~$ sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
[sudo] password for pawan: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 643DC6BD56580CEB1AB4A9F63B22AB97AF1CDFA9
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpg: key AF1CDFA9: "Launchpad PPA for Ubuntu-X" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
pawan@pawan:~$ 


The error with my ubuntu still flickers and goes weird.

---

### Post by pqwoerituytrueiwoq on 2011-06-11
did you install updates after?

---

### Post by pawan98 on 2011-06-11
I dont think so- how do you do that?

---

### Post by pqwoerituytrueiwoq on 2011-06-11
System->administration->update manager
there are 2 button you need check and install

---

### Post by pawan98 on 2011-06-11
No updates to install... looks like it don't work. If you know how to fix this [http://ubuntuforums.org/showthread.php?p=10927478](http://ubuntuforums.org/showthread.php?p=10927478) please tell me =]

---

### Post by pqwoerituytrueiwoq on 2011-06-11
try ubuntu classic
[http://www.liberiangeek.net/2011/04/change-classic-ubuntu-desktop-ubuntu-11-04-natty-narwhal/](http://www.liberiangeek.net/2011/04/change-classic-ubuntu-desktop-ubuntu-11-04-natty-narwhal/)

---

### Post by pawan98 on 2011-06-11
The whole point of making that thread was so I didn't have to use ubuntu classic and i could fix that

---

### Post by pqwoerituytrueiwoq on 2011-06-11
[https://launchpad.net/~unity/+archive/ppa](https://launchpad.net/~unity/+archive/ppa)
maybe that ppa will get unity working for you
if it makes it worse the other ppa (x-swap) has a package called ppa-purge that can undo it

---

### Post by pawan98 on 2011-06-11
nope - dont work

---

### Post by David006 on 2011-10-28
I'm having stability issues with an older HP d530 SFF PC, with **Intel 82865G** integrated graphics, under **Ubuntu 11.10 (Oneiric)** and Unity-2D.

from:
'Video not working properly on an integrated Intel 82865G card'
[http://askubuntu.com/questions/38144/video-not-working-properly-on-an-integrated-intel-82865g-card](http://askubuntu.com/questions/38144/video-not-working-properly-on-an-integrated-intel-82865g-card)

The steps to install older Intel driver are:

[b]sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install xserver-xorg-video-intel-2.4[/b]


**Note:** I can't get this to work for Ubuntu 11.10 (oneiric), but I think that is because the repository has not been updated past Ubuntu 11.04 (natty).

---

