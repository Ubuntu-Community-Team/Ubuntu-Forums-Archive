---
title: "RPM? Postfix?"
date: 2010-02-13
forum: General Help
---

### Post by jmcgovern on 2010-02-13
I noticed in an update i did today that a number of things from the 'distribution updates' category were marked as 'new install'.  Included in them were things like alien, Postfix, and RPM.  the RPM especially confuses me.  Is Ubuntu moving to being able to handle both package types?  As far as I can tell these were from the official updates. not some third party repository I've added.

---

### Post by gmargo on 2010-02-13
Don't worry, be happy. The **rpm** tool is not normally used but it's there for your convenience.  Suppose you wanted to pull apart a binary or source .rpm file from openSUSE or Mandriva? Think of it as just another tool like **zip**.  The **alien** tool allows package conversion to some extent to allow installing from an .rpm.

"alien" description:
Description: convert and install rpm and other packages
 Alien allows you to convert LSB, Red Hat, Stampede and Slackware Packages
 into Debian packages, which can be installed with dpkg.
 .
 It can also generate packages of any of the other formats.

---

### Post by jmcgovern on 2010-02-13
Oh I know exactly what the tools ARE, I learned Linux on RHEL. I was just trying to piece together WHY the Red Hat Package Manager was being included in a Debian-based distro.  I think the first part of your answer answers that question.

---

### Post by wiltzius on 2010-02-14
I'm curious about this too... for me it's not only postfix and alien, but a whole slew of stuff, including most of the QT libraries and other stuff I really don't want on my gnome/gtk+ based desktop.

But here's the really weird part... this is all in Update Manager. If I do:

$ sudo apt-get upgrade

then apt only wants to upgrade the packages that actually need upgrading, not install any new ones. I thought Update Manager essentially was just a front-end for this command, does it do different things? I checked in Synaptic to make sure nothing was "marked for installation" or anything. 

Anyone know what's up?

---

### Post by astoltz on 2010-02-14
For me, they were part of some new dependencies for the google chrome dev channel.  Don't know why the latest version added all the new dependencies, but I've dropped back to the stable version of chrome.

---

### Post by wiltzius on 2010-02-16
Yeah I just discovered the same thing. That's annoying; I like some of the features of the dev channel and it's been very stable. Hopefully they'll fix this. Thanks!

---

### Post by wiltzius on 2010-02-16
Thread on the Google support group about the problem; no response yet:

[http://bit.ly/9o1ENI](http://bit.ly/9o1ENI)

---

### Post by fireman biff on 2010-02-18
> **wiltzius said:**
> But here's the really weird part... this is all in Update Manager. If I do:

$ sudo apt-get upgrade

then apt only wants to upgrade the packages that actually need upgrading, not install any new ones. I thought Update Manager essentially was just a front-end for this command, does it do different things? I checked in Synaptic to make sure nothing was "marked for installation" or anything. 

Anyone know what's up?

When you tell apt-get to do an upgrade it will never install any new packages, only upgrade packages that are already installed. If upgrading one package requires installing something new, then that package will not get upgraded.

If you want apt-get to install new packages as required you need to tell it to do a dist-upgrade, which is more like using Update Manager:
```
sudo apt-get dist-upgrade
```

---

