---
title: "what are those dependencies??"
date: 2009-08-27
forum: General Help
---

### Post by sububtu on 2009-08-27
when i tried to install VLC , frm .deb file, i got an error msg , **dependency is not satisfiable: vlc-nox**, then i dwnldd vlc-nox & tried to install that , but tat vlc-nox, inturn depends on another file & when i tried to follow those dependenvis - it goes like a chain, 
the reason y im i dwnloaded those files and installed it with out using package manager assistance is , I dnt hav a high speed inet connection currently,is that possible to install manually

---

### Post by MaxIBoy on 2009-08-27
Usually it's best to use the package manager to install things, for exactly this reason. If you're worried about your internet connection being interrupted or something, this could be a problem I guess. But all those dependencies are important and necessary, so if you try to install without them it won't work anyway.

---

### Post by kpkeerthi on 2009-08-27
If you want to install a package offline (w/o internet), you need to track the dependencies and download them yourself. You can check a package's dependencies at [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by sububtu on 2009-08-27
Thanks!!

---

### Post by jerome1232 on 2009-08-27
The problem with that is somtimes those dependencies, have dependencies, which in turn have dependencies.

In short manually installing is a PITA. There's a program out there which can automatically do this stuff and put all of the packages on a usb stick or cd but I can't remember what it's called, it's not APTonCD it's another one.

I'm searching for it, it was really cool.

---

### Post by dk06 on 2009-08-27
****

**[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)**
> 

**VLC media player for [Ubuntu]("http://www.ubuntu.com/")**

    **1.0.0 on Jaunty Jackalope**

  In order to get the latest 1.0.0 on your latest ubuntu, you should use use a version from [PPA]("https://launchpad.net/ubuntu/+ppas"). There is an [howto to use a ppa]("https://help.launchpad.net/Packaging/PPA#Installing%20software%20from%20a%20PPA").
 The version can be found on: [https://launchpad.net/~c-korn/+archive/vlc](https://launchpad.net/~c-korn/+archive/vlc)
  [B]Ubuntu Jaunty Jackalope 9.04, 
Ubuntu Intrepid Ibex 8.10, 
Ubuntu Hardy Heron LTS 8.04[/B]

 Open Synaptic (System -> Administration -> Synaptic Package Manager). In Settings -> Repositories, make sure you have a "multiverse"  repository activated.
 Search for vlc and install it. You should also install vlc-plugin-esd, mozilla-plugin-vlc (and libdvdcss2).
  **Command line way**

 You need to check that a "multiverse" mirror is listed in your /etc/apt/sources.list.

```

% sudo apt-get update

```
```

% sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc

```



---

### Post by ptsubin on 2009-08-27
Nowadays people prefer aptitude over apt for many reasons.

sudo aptitude update
sudo aptitude install ------------

---

### Post by jerome1232 on 2009-08-27
found it!

[http://keryxproject.org/](http://keryxproject.org/)

It even runs on Windows.

---

### Post by dk06 on 2009-08-27
> **ptsubin said:**
> Nowadays people prefer aptitude over apt for many reasons.

sudo aptitude update
sudo aptitude install ------------


Ah Ha!

Okay, lol...Ubuntu isn't my primary OS (just here for fun) but thank you, I'm slacking on keeping up-to-date with the current debian/ubuntu methods.

(maybe it's time to post on the rhel/centos forums but like helping spread linux to people tired of paying MS for garbage & ubuntu seems to be the most popular distro)

Thanks again, take care

---

### Post by sububtu on 2009-08-28
Coool :guitar:, let me check, thanks...

---

