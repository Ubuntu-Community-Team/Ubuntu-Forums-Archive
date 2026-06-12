---
title: "Setting Up Ubuntu amd64"
date: 2011-01-10
forum: General Help
---

### Post by 01001101 on 2011-01-10
I've recently changed my processor to a 64-bit AMD processor. So, I've installed Ubuntu for AMD 64. But, I'm encountering some problems with basic functions that need to be fixed.

[LIST]
[*]I can't play flash videos. When I download the plug-in from adobe's site to install on Chrome. The software center says that I can't install it because it's i386. I can't find any download for one that's for AMD 64.
[*]I've never been able to get sun java installed on an ubuntu system.
[*]How in the world do you install [celtx]("http://www.celtx.com") on an Ubuntu system. It has the download, but I haven't been able to do it.
[*]How do I install the graphics drivers for a PNY Nvidia Quadro FX 580 graphics card. I know about the additional driver's section, but for some reason my computer can't boot when the card is in and I think it's due to the lack of drivers.
[/LIST]

Anyway, what would be great is if someone gave me a step-by step walk-through on how to install all of this stuff. Thanks.

---

### Post by 01001101 on 2011-01-10
I've recently changed my processor to a 64-bit AMD processor. So, I've installed Ubuntu for AMD 64. But, I'm encountering some problems with basic functions that need to be fixed.

[LIST]
[*]I can't play flash videos. When I download the plug-in from adobe's site to install on Chrome. The software center says that I can't install it because it's i386. I can't find any download for one that's for AMD 64.
[*]I've never been able to get sun java installed on an ubuntu system.
[*]How in the world do you install [celtx]("http://www.celtx.com") on an Ubuntu system. It has the download, but I haven't been able to do it.
[*]How do I install the graphics drivers for a PNY Nvidia Quadro FX 580 graphics card. I know about the additional driver's section, but for some reason my computer can't boot when the card is in and I think it's due to the lack of drivers.
[/LIST]

Anyway, what would be great is if someone gave me a step-by step walk-through on how to install all of this stuff. Thanks.

---

### Post by Sef on 2011-01-10
Moved to ABT.

---

### Post by Vaphell on 2011-01-10
flash - if you still have firefox around, install flash-aid plugin that will find and install 64bit plugin for you and chrome should pick it up (hopefully).
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)
you can install 32bit flash and it's in the repositories (flashplugin-installer/flashplugin-nonfree) but i had few problems and prefer native 64bit beta version.

java - it should be in partners repository. goto system > administration > software sources and check if you have it marked. When it's enabled, sun-java packages should be available to install

---

### Post by James_Lochhead on 2011-01-10
> **01001101 said:**
> 
[LIST]
[*]I can't play flash videos. When I download the plug-in from adobe's site to install on Chrome. The software center says that I can't install it because it's i386. I can't find any download for one that's for AMD 64.
[*]I've never been able to get sun java installed on an ubuntu system.
[*]How in the world do you install [celtx]("http://www.celtx.com") on an Ubuntu system. It has the download, but I haven't been able to do it.
[*]How do I install the graphics drivers for a PNY Nvidia Quadro FX 580 graphics card. I know about the additional driver's section, but for some reason my computer can't boot when the card is in and I think it's due to the lack of drivers.
[/LIST]


- The easiest way to install the flash player on Ubuntu AMD64 is to open a terminal (Accessories > Terminal) and type:

sudo apt-get -y install flashplugin-nonfree

Just copy this, paste it (terminal paste is ctrl shift p), hit enter, enter your password and lets it do its thing. A browser restart may be required.

- For Java, do the same as above but replace the command with.

sudo apt-get -y install sun-java6-jre

However, I *think* the open-jre is installed by default, therefore, you have to tell Ubuntu which one you want to use. Although there are other methods the easiest way is probably just to remove the open-jre.

sudo apt-get remove openjdk-6-jre
sudo apt-get autoremove

The first line removes the package, the second line removes any packages that are only needed for the openjdk-6-jre and are therefore no longer necessary.

- For celtx. Download it. It's a compressed archive (like a .zip). Right click it and select extract here. Go in to the directory and double click the file "celtx", that will start the application.

celtx is basically the equivalent of celtx.exe if you are more familiar with Windows systems.

There are other things you can do to integrate it a bit better (such as add a symbolic link in /bin and add it to applications etc etc) but they are a little more annoying and the program will run fine if you just leave it like that.

- Although I'm no expert the graphics card issue sounds more like an issue with the hardware than the software. As far as I am aware, a card without drivers should simply not be used and should not cause this kind of problem. Anyway to install the drivers:

sudo apt-get install nvidia-current

I doubt it will fix your problem though.

---

### Post by JBAlaska on 2011-01-10
Open a terminal and do:

```
sudo add-apt-repository ppa:sevenmachines/flash
sudo apt-get update
sudo apt-get install flashplugin64-installer
```

---

### Post by jmszr on 2011-01-10
This post is being answered here: [http://ubuntuforums.org/showthread.php?p=10338008](http://ubuntuforums.org/showthread.php?p=10338008)

Moderators, please merge.

---

### Post by s.fox on 2011-01-10
Please do not create multiple threads about the same problem. Thank you.

Threads merged.

---

### Post by oldos2er on 2011-01-10
> **James_Lochhead said:**
> - The easiest way to install the flash player on Ubuntu AMD64 is to open a terminal (Accessories > Terminal) and type:

sudo apt-get -y install flashplugin-nonfree



Unfortunately that gives one 32-bit flash + nspluginwrapper. Much better on a 64-bit system to install 64-bit flash; click the FlashAid link in my sig.

---

