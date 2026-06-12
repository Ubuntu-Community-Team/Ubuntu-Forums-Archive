---
title: "ubuntu 64 bit"
date: 2012-03-09
forum: General Help
---

### Post by Rakeshvijayan on 2012-03-09
HI I have a doubt ,is it ubuntu-restricted-extras command will install flash player by default on ubuntu11.10 64 bit os 
waiting for quick replay friends

---

### Post by plucky on 2012-03-09
> **Rakeshvijayan said:**
> HI I have a doubt ,is it ubuntu-restricted-extras command will install flash player by default on ubuntu11.10 64 bit os 
waiting for quick replay friends

Ubuntu-restricted-extras is not a command,it is a package that is installed using the Software Center,apt-get or synaptic.
 
> This package depends on some commonly used packages in the Ubuntu
multiverse repository.

Installing this package will pull in support for MP3 playback and decoding,
support for various other audio formats (GStreamer plugins), Microsoft fonts,
Java runtime environment, Flash plugin, LAME (to create compressed audio
files), and DVD playback.

Good Luck

---

### Post by oldos2er on 2012-03-09
> **Rakeshvijayan said:**
> HI I have a doubt ,is it ubuntu-restricted-extras command will install flash player by default on ubuntu11.10 64 bit os 
waiting for quick replay friends

You can use **aptitude show <package>** (if you have aptitude installed), as well as Synaptic Package Manager to show package information.

Or you can visit packages.ubuntu.com. The package ubuntu-restricted-extras depends on ubuntu-restricted-addons, which shows it installs flashplugin-installer [amd64]. See [http://packages.ubuntu.com/oneiric/ubuntu-restricted-addons](http://packages.ubuntu.com/oneiric/ubuntu-restricted-addons)

---

### Post by Rakeshvijayan on 2012-03-10
I mean,do it possible to run that package on ubuntu 64 bit .

---

### Post by plucky on 2012-03-10
> **Rakeshvijayan said:**
> I mean,do it possible to run that package on ubuntu 64 bit .

Yes

Just search for the package in the Software Centre and install it.

Good Luck

---

