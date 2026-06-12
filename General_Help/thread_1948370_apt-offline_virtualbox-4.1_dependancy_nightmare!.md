---
title: "apt-offline virtualbox-4.1 dependancy nightmare!"
date: 2012-03-28
forum: General Help
---

### Post by Technosites on 2012-03-28
Hi,

I'm trying to install virtualbox-4.1 on an offline headless Ubuntu 11.10 Server and after hours and hours of trying different approaches, I still can't get it working.

apt-get -d isn't working right as my ubuntu box with an internet connection is 32bit not amd64 like the server is. Same problem with aptoncd.

Trying to download all the dependencies and dpkg -i manually isn't getting anywhere, as the dependencies all have dependencies! Even with apt-cdrom add the original install cd, getting no where.

apt-offline looks like the approach I want, but apt-offline set vbox-offline.sig --install-packages virtualbox-4.1 --src-build-dep --install-src-packages virtualbox-4.1 fails with 'virtualbox-4.1' has no install candidate. Even adding the virtualbox deb repo into sources.list and running an apt-offline update/upgrade cycle doesn't seem to add virtualbox-4.1 into apt-cache.

synaptic generate download script is not help because i'm running headless, no gui.

Keryx seems to be gui only as well.

All help is very much appreciated! Basically, how do I run dpkg -i virtualbox-4.1, get it to save the list of dependencies (and their dependencies) into apt-get upgrade, run apt-offline set to generate a sig with everything I need so I can apt-offline get on my online box?

Many Thanks!
-tech

---

### Post by cortman on 2012-03-28
How badly do you want virtualbox?

I've wondered the same thing for some time myself- a command line version of Synaptic's download scripts.
I'm not very knowledgeable, but with dependencies lacking dependencies, you may just have to figure out the dependent packages for each dependent package, which can be very time consuming, but possibly the only way.
Also, before you do much else, run

```
sudo apt-get install -f
sudo apt-get clean
```

to clean out the package system of any partially installed packages, etc.

---

### Post by Technosites on 2012-03-28
I guess the thing to do would be to put the same generate download script functionality that synaptic's gui has into aptitude maybe?

Virtualbox is the main function of the server, so yeah :) Turned out to be quicker to persuade the network admin to set me up with a switch and let me connect into the network, which with an internet connection I can now see that just over half a gig of dependencies were actually required for Virtualbox! So either Virtualbox is coded really badly, or Ubuntu Server base install comes with nothing :P Irony is that most the dependencies seem to be for the virtualbox gui, when I'm only wanted to use VBoxHeadless but nevermind!

Thanks for the input,
-tech

---

### Post by cortman on 2012-03-28
Well I'm glad you were able to resolve it the easy way! I hope you got updates, etc., downloaded for your server too while you were at it. I'm not sure why VBox required so many dependencies.

---

