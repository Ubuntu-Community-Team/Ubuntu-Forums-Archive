---
title: "unsatisfiable dependency when installing Flash 10"
date: 2009-08-23
forum: General Help
---

### Post by beezum88@gmail.com on 2009-08-23
So I downloaded the package from adobe's site to install Flash 10 on ubuntu 9.04.  Firefox automatically opened it with the package installer and everything looked like it was going to work, but then I got an error: "Error: Dependency is not satisfiable: libnspr4-dev".  Any idea how to fix this? 

By the way, I'm a relative newbie at linux, so bear that in mind when you answer :-)

---

### Post by TeoBigusGeekus on 2009-08-23
System -> Administration -> Synaptic package manager
Search for libnspr4-dev. When found, right click it and mark it for installation.
That's it.
Also, instead of going to Adobe's site, do also a search for flash in Synaptic. I think Flash 10.0 is listed there.

---

### Post by beezum88@gmail.com on 2009-08-23
Thanks!  It installed, but I went with the package from adobe's site because I couldn't find it in Synaptic.  

Of course, the youtube video I tested it on doesn't play all that well (1 or 2 fps frame rate), but that could be because I have a 12 year old computer with only 256MB of ram.

---

### Post by TeoBigusGeekus on 2009-08-23
I wonder when the flash problem is going to be solved in Ubuntu...:-k

---

### Post by jkcohen on 2009-10-03
The solution of installing libnspr4-dev to satisfy the dependency required by Flash 10 will not work, because libnspr4-dev cannot be installed from Synaptic; apt says that it has been superseded by libnspr4-0d. Flash 10 remains unsatisfied. How to satisfy it and get it to install from the Adobe site? (The version in the Ubuntu repositories does not have the latest security fixes.)

---

### Post by mc4man on 2009-10-03
> The solution of installing libnspr4-dev to satisfy the dependency required by Flash 10 will not work, because libnspr4-dev cannot be installed from Synaptic; apt says that it has been superseded by libnspr4-0d

Those are 2 separate, but dependant packages, libnspr4-dev depends on libnspr4-0d with a limited version range

Go to System -> Admin.. -> Software Sources and under the update tab make sure that the first 2 choices are enabled (security and recommended) If not, enable, close and reload

Otherwise run sudo apt-get update and ck again


relevant jaunty package pages

[http://packages.ubuntu.com/jaunty-updates/libnspr4-dev](http://packages.ubuntu.com/jaunty-updates/libnspr4-dev)
[http://packages.ubuntu.com/jaunty-updates/libnspr4-0d](http://packages.ubuntu.com/jaunty-updates/libnspr4-0d)

---

### Post by myislanduniverse on 2009-10-31
That's all well and good, but when I try to install libnspr4-dev (which can't be found on Synaptic, btw), it tells me that it can't satisfy the dependency: libnspr4-0d, which is installed.

I always know when I unwrap a fresh new Linux that I'm going to be spending the next two days straight trying to get it to run...  :-/

---

### Post by myislanduniverse on 2009-10-31
A good ole' 

sudo apt-get install flashplugin-free

Installed everything without issue.  Hmm.  <shrug>

---

### Post by mrebanza on 2009-12-08
fresh install on ubuntu today . . . . sudo apt-get update did the trick for the flash dependency . .. . . THANKS . . . . also guys don't make the mistake of trying to download the gnome and linux free verison of flash . . . they are out dates and do not function half as good as Adobe Official . . . . Dont get me wrong . . . . these were GREAT at the time they were release because flash had refused to develop a linux version (and I think these projects helped put the fire under their *** too get the linux ball rolling) but like I said they are outdated and you will be disappointed

---

