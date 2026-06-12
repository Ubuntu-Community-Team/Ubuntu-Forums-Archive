---
title: "apt-get Ign"
date: 2010-08-15
forum: General Help
---

### Post by bprins on 2010-08-15
Hi,

Short question. What does Ign means when I am running sudo apt-get update:
```

bas@ubuntu-lt:~$ sudo apt-get update | grep Ign | grep xbmc
Ign http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/ lucid/main Translation-en_US

```
Thanks!

Bas

---

### Post by mhgsys on 2010-08-15
Ignore

---

### Post by Smart Viking on 2010-08-15
It means that it will ignore the repo, when you launch apt-get update it will download a little file(DiffIndex) which will tell you the differences in the repos since you last updated(i think), and if there is no change in a repo it will say "Ign". Anyway, it is nothing wrong, it is the way it should be. :)

---

### Post by bprins on 2010-08-15
Ok, I figured that much.

What does that mean? Why is it ignoring repositories? Because I'm not able to install xbmc after adding it's repo (and key).

---

### Post by bprins on 2010-08-15
> **Smart Viking said:**
> It means that it will ignore the repo, when you launch apt-get update it will download a little file(DiffIndex) which will tell you the differences in the repos since you last updated(i think), and if there is no change in a repo it will say "Ign". Anyway, it is nothing wrong, it is the way it should be. :)

aha, yo. thanks.

then I'll have to search further because it still wont let me install xbmc :)

Thanks I'll close the thread.

Bas

---

### Post by mhgsys on 2010-08-15
[http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide](http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide)

---

### Post by bprins on 2010-08-15
bas@ubuntu-lt:~$ sudo apt-get install xbmc-
xbmc-bin          xbmc-data         xbmc-test-helper  
xbmc-common       xbmc-ppa-keyring  

that what Im allowed to install. It doesnt list xbmc nor xbmc-standalone.

I've added the repos. (and ran sudo apt-get update ofc)

:)

---

### Post by mhgsys on 2010-08-15
I see, 

I'm trying the same thing to help you out.. 

Weird though... I have xbmc running fine on 10.04 on a other computer here.
(remote controlled and everything)

---

### Post by bprins on 2010-08-15
:)

appreciated.

I just removed it this morning because my HDMI device wasnt working from XBMC anymore. So thought lets try the "nuke" method and reinstall all, but I guess that wasnt to helpful.

Nevermind, I'll give it a new try this evening.

Thanks all tho.

Bas

---

### Post by mhgsys on 2010-08-15
Found the solution!

```
sudo add-apt-repository ppa:team-xbmc-svn/ppa
```

```
sudo apt-get update
```

after doing that;

xbmc will install fine.


[quote=]mhg@mhg-desktop:~$ sudo apt-get install xbmc xbmc-standalone 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libass4 libfaad2 libglew1.5 libmad0 libmicrohttpd5 libmikmod2 libmms0
  libmng1 libmodplug0c2 libmpeg2-4 libpcrecpp0 libqt3-mt librtmp0
  libsdl-image1.2 libsdl-mixer1.2 libsmpeg0 libvdpau1 python-qt3 python-sip
  xbmc-bin xbmc-data xbmc-skin-confluence xbmc-web
Suggested packages:
  glew-utils libqt3-mt-psql libqt3-mt-mysql libqt3-mt-odbc nvidia-vdpau-driver
  vdpau-driver python-qt3-gl python-qt3-doc xbmc-third-parties
  xbmc-test-helper
The following NEW packages will be installed:
  libass4 libfaad2 libglew1.5 libmad0 libmicrohttpd5 libmikmod2 libmms0
  libmng1 libmodplug0c2 libmpeg2-4 libpcrecpp0 libqt3-mt librtmp0
  libsdl-image1.2 libsdl-mixer1.2 libsmpeg0 libvdpau1 python-qt3 python-sip
  xbmc xbmc-bin xbmc-data xbmc-skin-confluence xbmc-standalone xbmc-web
0 upgraded, 25 newly installed, 0 to remove and 11 not upgraded.
Need to get 44.5MB of archives.
After this operation, 100MB of additional disk space will be used.
Do you want to continue [Y/n]? 
[/quote]

---

### Post by bprins on 2010-08-15
hah!

my hero.

thanks mate :)) that did the trick.

---

### Post by mhgsys on 2010-08-15
> **bprins said:**
> hah!

my hero.

thanks mate :)) that did the trick.

Nice!

 **Someone should change the repo in that howto'**

```
sudo add-apt-repository ppa:team-xbmc
```

should be in fact

```
sudo add-apt-repository ppa:team-xbmc-svn/ppa
```

---

