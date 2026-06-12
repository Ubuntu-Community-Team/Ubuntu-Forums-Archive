---
title: "Looking for a current version of Flight Gear"
date: 2009-08-28
forum: General Help
---

### Post by Vince N on 2009-08-28
Hey Guys,

Running 9.04.  I was in another thread that made me think of flight gear and I wanted to see how they've come since the last time I saw them.  Unfortunatly I noted that the version in the ubuntu repositories is quite old.  Does anyone know how I can get the latest version on here and running short of downloading and compiling everything?

---

### Post by jpeddicord on 2009-08-28
Ubuntu Karmic (9.10 in October) has FlightGear 1.9.1, which is the current version. You can either wait for that to be released and upgrade, or try to install the Karmic version into Jaunty (at your own risk, though there shouldn't be any problems).

The package listing has more information and binaries you can download:
[https://launchpad.net/ubuntu/+source/flightgear/1.9.1-1ubuntu1](https://launchpad.net/ubuntu/+source/flightgear/1.9.1-1ubuntu1)

---

### Post by Vince N on 2009-08-28
IS there an easy way to do this?  I'm a little reluctant to enable the whole Karmic repository for one program.

---

### Post by jpeddicord on 2009-08-28
> **Vince N said:**
> IS there an easy way to do this?  I'm a little reluctant to enable the whole Karmic repository for one program.

You don't have to. On the link I posted click the appropriate arch under Builds. On the page after that, look on the bottom-right for "Built files" where you'll find a package you can download.

---

### Post by Vince N on 2009-08-28
Oh, Duh.... Sorry  Thanks for that :-)

---

### Post by xeddog on 2009-09-02
I just tried installing the Karmic version of flightgear (flightgear_1.9.1-1ubuntu1_i386.deb) on my Jaunty system and received the following message in gdebi package installer.

> "Error: Dependency is not satisfiable: libopenscenegraph56 (>= 2.8.1)"

xeddog

---

### Post by visionary on 2009-09-23
Hello ....

**[COLOR="Blue"]The Good news is, now we have Flight gear DEB files available for easy installation for 9.04. Visit [www.unitedfreeworld.com](www.unitedfreeworld.com) , the site is known for it's free Flightgear Add ons and scripts.[/COLOR]** i downloaded and installed from [www.unitedfreeworld.com](www.unitedfreeworld.com) the Flightgear DEB files which worked perfectly.Together with Flightgear, it also comes with FGRUN And FGCOM...in another words, you have the GUI(FGRUN), The SIM(FLightgear), The VOICE chat(FGCOM).

There is also a script for those who want to download and compile install CVS Flightgear.

:)

---

### Post by razzbar on 2009-11-03
> **jpeddicord said:**
> Ubuntu Karmic (9.10 in October) has FlightGear 1.9.1, which is the current version. You can either wait for that to be released and upgrade, or try to install the Karmic version into Jaunty (at your own risk, though there shouldn't be any problems).

The package listing has more information and binaries you can download:
[https://launchpad.net/ubuntu/+source/flightgear/1.9.1-1ubuntu1](https://launchpad.net/ubuntu/+source/flightgear/1.9.1-1ubuntu1)

[SIZE=2]**Caveat emptor:**[/SIZE] I read this news and rejoiced, and took the network upgrade option to install 9.10. During the installation process, I got some error messages warning me of being unable to upgrade fgfs-base. The final result was an installation which "may be unusable". Well, it's usable, but I can neither install, upgrade, or remove flightgear now, through the new package manager. I am also getting other problems. I've gone from a good installation of 9.04 to a buggy 9.10, and can't do anything with flightgear. 

I'm considering a new install of 9.10 from CD. I think it could take a very long time to go thru my system with a magnifying glass and tweezers to clean up the mess. 

**Conclusion**: If you've tried to upgrade flightgear while running 9.04, and have failed, be ready to fail again in a bigger way when you try a network upgrade.

---

