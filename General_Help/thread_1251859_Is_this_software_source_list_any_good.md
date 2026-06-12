---
title: "Is this software source list any good?"
date: 2009-08-28
forum: General Help
---

### Post by Scubdup on 2009-08-28
I've just installed Jaunty on a fresh install. I remember having a few sources added to an old source.list but can't remember what they were.

I found [this article]("http://theindexer.wordpress.com/2009/04/24/to-do-list-after-installing-ubuntu-904-aka-jaunty-jackalope/") with [this list]("http://files.getdropbox.com/u/1402212/jaunty.sources.list") and thought it looked good, but I was wondering if there were any problems with it.

The To Do list in that article is quite useful as far as I'm concerned. I found it while thinking about how I always have to do a number of things to Ubuntu after installation to get it where I want, and how it'd be useful to automate as much as possible...

My list is cuurently something like:-

Install Ubuntu
Add software sources
Add software
Install codecs
Install themes, desktop, icons
Customise Docky, firefox (plan to use firefox addon FEBE to store addons, and foxmarks to store bookmarks)

Trying to come up with ways and means to shorten the time and decrease the hassleinvolved.

---

### Post by slakkie on 2009-08-28
Looks ok to me, you can remove most of the ppa stuff if you don't use it..

---

### Post by hal10000 on 2009-08-28
See [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) . It's a good guide for using repositories.
---------
Here's my /etc/apt/sources.list, with some third party, backports and medibuntu etc. packages enabled:
> 
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) jaunty main restricted

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) jaunty-updates universe

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) jaunty partner
deb-src [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) jaunty partner

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security multiverse

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) jaunty-proposed restricted main multiverse universe
deb [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty free non-free
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) jaunty non-free
deb [http://ppa.launchpad.net/debichem/ubuntu](http://ppa.launchpad.net/debichem/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/debichem/ubuntu](http://ppa.launchpad.net/debichem/ubuntu) jaunty main
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) jaunty main


---

### Post by gastly on 2009-08-28
I use this tool [here](http://repogen.simplylinux.ch/) to generate a sources.list for a new system. It works for me :)

---

### Post by Scubdup on 2009-08-28
Thanks for the resources. I love that list generator - very handy.

---

