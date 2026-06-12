---
title: "Need to install package from Hoary's repositories"
date: 2005-03-15
forum: General Help
---

### Post by Campitor on 2005-03-15
Hello:

  I do scientific computing and need an excellent plotting software.  I've checked the web-pages and GRACE seems to be the best option (scigraphics would always crash on my system..don't know why?).  I run Warty, and Grace is not available on Warty's repositories.  I saw that GRACE is available at Hoary's Universe.

  I'm a big newbie at apt-get, I've checked this webpage

[HTML]http://www.ubuntulinux.org/wiki/PinningHowto[/HTML]

and did not feel confortably enough to actually do this.  And BTW, I dont have a: /etc/apt/apt.conf file , and did not know how to create one?  Is there any easy way, that I can just install grace from Hoary, and not update the hole system, or do major changes to my apt.config file?  Can I just include the Hoary repository, install grace and then just uncheck it from the synaptic -> repository menu?  How about dependencies?  Any help would be highly appreciat it!!!

thanks,

Camp.

---

### Post by Campitor on 2005-03-15
Ok...this is what i've done so far:
1. Created the file  /etc/apt/preference  and added this to it:
```
Package: *
Pin: release a=warty
Pin-Priority: 700

Package: *
Pin: release a=hoary
Pin-Priority: 650
```

2.  Added the following repositories to my sources.list file:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe

   ***comment:  I did not remove any of the warty or nerim repositories***

3.  typed
```
sudo apt-get update
sudo apt-get -y install grace6

```
and this is the error I get:
```
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  grace6: Depends: libexpat1 (>= 1.95.8) but 1.95.6-8 is to be installed
E: Broken packages
```

I think I'm close...but the library libexpat1 is stopping me.  Can anyone help...please? 

thanks

Campitor

---

### Post by the Blow Leprechaun on 2005-03-15
I assume you've tried to apt-get install libexpat1? I have it available to me in Synaptic... I used to have it installed, too.

---

### Post by Campitor on 2005-03-16
[QUOTE=the Blow Leprechaun]I assume you've tried to apt-get install libexpat1? I have it available to me in Synaptic... I used to have it installed, too.[/QUOTE]
 Yes..I have libexpat1 installed, the problem is, that my installed version: 1.95.6-8(probably from Warty), but the grace6 package needs version 1.95.8, which is not availble to me (for some reason).  Maybe I need to add the multiverse repository from Hoary too...I don't know.  Or maybe I need to uninstall my previous version of libexpat1 or upgrade...but I don't know how to upgrade just one package to Hoary's version.  I'll keep trying.

Camp.

---

