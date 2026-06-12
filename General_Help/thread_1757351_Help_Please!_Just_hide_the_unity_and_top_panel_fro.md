---
title: "Help Please! Just hide the unity and top panel from 11.04"
date: 2011-05-13
forum: General Help
---

### Post by masud7827 on 2011-05-13
After I delete those screen-short software, my unity bar goes hide and never come, please help here is the picture which i delete.

[IMG]http://i.imgur.com/eebzP.png[/IMG]

Now using classic desktop but i want to use unity but it comes only the full wallpaper and no bar comes. If i right click the mouse it works but where i can show the bar?

---

### Post by ivanovnegro on 2011-05-13
If you removed Compiz, reinstall it, you need it to run the Unity desktop.
To set the system back to default type in the terminal:

```
unity --reset
```

---

### Post by masud7827 on 2011-05-13
I installed compiz again, Should i need to set all compiz option to default value? I don't have them.  Here is the output, But the unity don't comes :(

And after i put the commend the unity is not installed :(

                                 masud@masud-desktop:~$ unity --reset
 The program 'unity' is currently not installed.  You can install it by typing:
 sudo apt-get install unity
 masud@masud-desktop:~$ sudo apt-get install unity
 [sudo] password for masud:  
 Reading package lists... Done
 Building dependency tree        
 Reading state information... Done
 Some packages could not be installed. This may mean that you have
 requested an impossible situation or if you are using the unstable
 distribution that some required packages have not yet been created
 or been moved out of Incoming.
 The following information may help to resolve the situation:
 

 The following packages have unmet dependencies:
  unity : Depends: libindicator2 but it is not going to be installed
          Depends: libnux-0.9-0 (>= 0.9.22) but it is not going to be installed
          Depends: libnux-0.9-0 (< 0.9.24) but it is not going to be installed
          Depends: unity-common (= 3.4.2-0ubuntu2) but 3.8.10-0ubuntu2 is to be installed
 E: Broken packages
  masud@masud-desktop:~$

---

### Post by ivanovnegro on 2011-05-13
Ok, now try unity --reset again, because now you have it back installed and later go to the Synaptic Package Manager-> Edit-> Repair broken packages, from the menu there.

---

### Post by masud7827 on 2011-05-13
after paste that it again showes

masud@masud-desktop:~$ unity --reset
The program 'unity' is currently not installed.  You can install it by typing:
sudo apt-get install unity
masud@masud-desktop:~$ 



:(

---

### Post by ivanovnegro on 2011-05-13
Are you in the Classic mode at the moment?
If so, logout and login into the Ubuntu Unity session.

---

### Post by masud7827 on 2011-05-13
Yes, I was in classic mode, but I just tried from unity mode also, it isn't working.

Same thing showing, If i tried to install from it software center It is showing [this error]("http://i.imgur.com/c9p6A.png") :(

---

### Post by ivanovnegro on 2011-05-13
Hm, what the hell is going on?
Can you put here your sources list with this command:

```
 cat /etc/apt/sources.list
```

---

### Post by masud7827 on 2011-05-13
Here is it

masud@masud-desktop:~$  cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) natty universe
deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://bd.archive.ubuntu.com/ubuntu/](http://bd.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
masud@masud-desktop:~$ ^C
masud@masud-desktop:~$

---

### Post by masud7827 on 2011-05-13
I just figure out and  works, very very thanks to you, It was the problem with Software Centre>Edit>Preferences>Server and I changed the USA server and it works :)

Again thanks :)

---

### Post by ivanovnegro on 2011-05-13
Ah, ok, yes, your sources list is in a perfect condition.

---

